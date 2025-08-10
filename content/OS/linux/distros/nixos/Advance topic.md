# [Remote Builds](https://nixos.org/manual/nix/unstable/advanced-topics/distributed-builds#remote-builds)

Nix supports remote builds, where a local Nix installation can forward Nix builds to other machines. This allows multiple builds to be performed in parallel and allows Nix to perform multi-platform builds in a semi-transparent way. For instance, if you perform a build for a `x86_64-darwin` on an `i686-linux` machine, Nix can automatically forward the build to a `x86_64-darwin` machine, if available.

To forward a build to a remote machine, it’s required that the remote machine is accessible via SSH and that it has Nix installed. You can test whether connecting to the remote Nix instance works, e.g.

```bash
$ nix store ping --store ssh://mac
```

will try to connect to the machine named `mac`. It is possible to specify an SSH identity file as part of the remote store URI, e.g.

```bash
$ nix store ping --store ssh://mac?ssh-key=/home/alice/my-key
```

Since builds should be non-interactive, the key should not have a passphrase. Alternatively, you can load identities ahead of time into `ssh-agent` or `gpg-agent`.

If you get the error

```bash
bash: nix-store: command not found error: cannot connect to 'mac'
```

then you need to ensure that the `PATH` of non-interactive login shells contains Nix.

> **Warning**
> 
> If you are building via the Nix daemon, it is the Nix daemon user account (that is, `root`) that should have SSH access to a user (not necessarily `root`) on the remote machine.
> 
> If you can’t or don’t want to configure `root` to be able to access the remote machine, you can use a private Nix store instead by passing e.g. `--store ~/my-nix` when running a Nix command from the local machine.

The list of remote machines can be specified on the command line or in the Nix configuration file. The former is convenient for testing. For example, the following command allows you to build a derivation for `x86_64-darwin` on a Linux machine:

```bash
$ uname 
Linux 

$ nix build --impure \   
	--expr '(with import <nixpkgs> { system = "x86_64-darwin"; }; runCommand "foo" {} "uname > $out")' \   
	--builders 'ssh://mac x86_64-darwin' 
[1/0/1 built, 0.0 MiB DL] building foo on ssh://mac 

$ cat ./result 
Darwin
```

It is possible to specify multiple builders separated by a semicolon or a newline, e.g.

  ```bash
  --builders 'ssh://mac x86_64-darwin ; ssh://beastie x86_64-freebsd'
  ```

Each machine specification consists of the following elements, separated by spaces. Only the first element is required. To leave a field at its default, set it to `-`.

1. The URI of the remote store in the format `ssh://[username@]hostname`, e.g. `ssh://nix@mac` or `ssh://mac`. For backward compatibility, `ssh://` may be omitted. The hostname may be an alias defined in your `~/.ssh/config`.
    
2. A comma-separated list of Nix platform type identifiers, such as `x86_64-darwin`. It is possible for a machine to support multiple platform types, e.g., `i686-linux,x86_64-linux`. If omitted, this defaults to the local platform type.
    
3. The SSH identity file to be used to log in to the remote machine. If omitted, SSH will use its regular identities.
    
4. The maximum number of builds that Nix will execute in parallel on the machine. Typically this should be equal to the number of CPU cores. For instance, the machine `itchy` in the example will execute up to 8 builds in parallel.
    
5. The “speed factor”, indicating the relative speed of the machine. If there are multiple machines of the right type, Nix will prefer the fastest, taking load into account.
    
6. A comma-separated list of _supported features_. If a derivation has the `requiredSystemFeatures` attribute, then Nix will only perform the derivation on a machine that has the specified features. For instance, the attribute
    
    ```
    requiredSystemFeatures = [ "kvm" ];
    ```
    
    will cause the build to be performed on a machine that has the `kvm` feature.
    
7. A comma-separated list of _mandatory features_. A machine will only be used to build a derivation if all of the machine’s mandatory features appear in the derivation’s `requiredSystemFeatures` attribute.
    
8. The (base64-encoded) public host key of the remote machine. If omitted, SSH will use its regular known-hosts file. Specifically, the field is calculated via `base64 -w0 /etc/ssh/ssh_host_ed25519_key.pub`.
    

For example, the machine specification

```
nix@scratchy.labs.cs.uu.nl  i686-linux      /home/nix/.ssh/id_scratchy_auto        8 1 kvm 
nix@itchy.labs.cs.uu.nl     i686-linux      /home/nix/.ssh/id_scratchy_auto        8 2 
nix@poochie.labs.cs.uu.nl   i686-linux      /home/nix/.ssh/id_scratchy_auto        1 2 kvm benchmark
```

specifies several machines that can perform `i686-linux` builds. However, `poochie` will only do builds that have the attribute

```
requiredSystemFeatures = [ "benchmark" ];
```

or

```
requiredSystemFeatures = [ "benchmark" "kvm" ];
```

`itchy` cannot do builds that require `kvm`, but `scratchy` does support such builds. For regular builds, `itchy` will be preferred over `scratchy` because it has a higher speed factor.

Remote builders can also be configured in `nix.conf`, e.g.

```
builders = ssh://mac x86_64-darwin ; ssh://beastie x86_64-freebsd
```

Finally, remote builders can be configured in a separate configuration file included in `builders` via the syntax `@file`. For example,

```
builders = @/etc/nix/machines
```

causes the list of machines in `/etc/nix/machines` to be included. (This is the default.)

If you want the builders to use caches, you likely want to set the option `builders-use-substitutes` in your local `nix.conf`.

To build only on remote builders and disable building on the local machine, you can use the option `--max-jobs 0`.
# [Tuning Cores and Jobs](https://nixos.org/manual/nix/unstable/advanced-topics/cores-vs-jobs#tuning-cores-and-jobs)

Nix has two relevant settings with regards to how your CPU cores will be utilized: `cores` and `max-jobs`. This chapter will talk about what they are, how they interact, and their configuration trade-offs.

- `max-jobs`  
    Dictates how many separate derivations will be built at the same time. If you set this to zero, the local machine will do no builds. Nix will still substitute from binary caches, and build remotely if remote builders are configured.
    
- `cores`  
    Suggests how many cores each derivation should use. Similar to `make -j`.
    

The `cores` setting determines the value of `NIX_BUILD_CORES`. `NIX_BUILD_CORES` is equal to `cores`, unless `cores` equals `0`, in which case `NIX_BUILD_CORES` will be the total number of cores in the system.

The maximum number of consumed cores is a simple multiplication, `max-jobs` * `NIX_BUILD_CORES`.

The balance on how to set these two independent variables depends upon each builder's workload and hardware. Here are a few example scenarios on a machine with 24 cores:

|`max-jobs`|`cores`|`NIX_BUILD_CORES`|Maximum Processes|Result|
|---|---|---|---|---|
|1|24|24|24|One derivation will be built at a time, each one can use 24 cores. Undersold if a job can’t use 24 cores.|
|4|6|6|24|Four derivations will be built at once, each given access to six cores.|
|12|6|6|72|12 derivations will be built at once, each given access to six cores. This configuration is over-sold. If all 12 derivations being built simultaneously try to use all six cores, the machine's performance will be degraded due to extensive context switching between the 12 builds.|
|24|1|1|24|24 derivations can build at the same time, each using a single core. Never oversold, but derivations which require many cores will be very slow to compile.|
|24|0|24|576|24 derivations can build at the same time, each using all the available cores of the machine. Very likely to be oversold, and very likely to suffer context switches.|

It is up to the derivations' build script to respect host's requested cores-per-build by following the value of the `NIX_BUILD_CORES` environment variable.
# [Verifying Build Reproducibility](https://nixos.org/manual/nix/unstable/advanced-topics/diff-hook#verifying-build-reproducibility)

You can use Nix's `diff-hook` setting to compare build results. Note that this hook is only executed if the results differ; it is not used for determining if the results are the same.

For purposes of demonstration, we'll use the following Nix file, `deterministic.nix` for testing:

```nix
let   
	inherit (import <nixpkgs> {}) runCommand; 
in {   
	stable = runCommand "stable" {} ''     
		touch $out   
	'';    
	unstable = runCommand "unstable" {} ''     
		echo $RANDOM > $out   
	''; 
}
```

Additionally, `nix.conf` contains:

```conf
diff-hook = /etc/nix/my-diff-hook 
run-diff-hook = true
```

where `/etc/nix/my-diff-hook` is an executable file containing:

```
#!/bin/sh 
exec >&2 
echo "For derivation $3:" 
/run/current-system/sw/bin/diff -r "$1" "$2"
```

The diff hook is executed by the same user and group who ran the build. However, the diff hook does not have write access to the store path just built.

## [Spot-Checking Build Determinism](https://nixos.org/manual/nix/unstable/advanced-topics/diff-hook#spot-checking-build-determinism)

Verify a path which already exists in the Nix store by passing `--check` to the build command.

If the build passes and is deterministic, Nix will exit with a status code of 0:

```bash
$ nix-build ./deterministic.nix --attr stable 
this derivation will be built:   
	/nix/store/z98fasz2jqy9gs0xbvdj939p27jwda38-stable.drv 
building '/nix/store/z98fasz2jqy9gs0xbvdj939p27jwda38-stable.drv'... /nix/store/yyxlzw3vqaas7wfp04g0b1xg51f2czgq-stable 

$nix-build ./deterministic.nix --attr stable --check 
checking outputs of '/nix/store/z98fasz2jqy9gs0xbvdj939p27jwda38-stable.drv'... 
/nix/store/yyxlzw3vqaas7wfp04g0b1xg51f2czgq-stable
```

If the build is not deterministic, Nix will exit with a status code of 1:

```bash
$ nix-build ./deterministic.nix --attr unstable 
this derivation will be built:   
	/nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv 
building '/nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv'... 
/nix/store/krpqk0l9ib0ibi1d2w52z293zw455cap-unstable 

$ nix-build ./deterministic.nix --attr unstable --check 
checking outputs of '/nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv'... 
error: derivation '/nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv' 
may not be deterministic: output '/nix/store/krpqk0l9ib0ibi1d2w52z293zw455cap-unstable' differs
```

In the Nix daemon's log, we will now see:

```log
For derivation /nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv: 
1c1 
< 8108 
--- 
> 30204
```

Using `--check` with `--keep-failed` will cause Nix to keep the second build's output in a special, `.check` path:

```bash
$ nix-build ./deterministic.nix --attr unstable --check --keep-failed 
checking outputs of '/nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv'... 
note: keeping build directory '/tmp/nix-build-unstable.drv-0' 
error: derivation '/nix/store/cgl13lbj1w368r5z8gywipl1ifli7dhk-unstable.drv' 
may not be deterministic: output '/nix/store/krpqk0l9ib0ibi1d2w52z293zw455cap-unstable' differs 
from '/nix/store/krpqk0l9ib0ibi1d2w52z293zw455cap-unstable.check'
```

In particular, notice the `/nix/store/krpqk0l9ib0ibi1d2w52z293zw455cap-unstable.check` output. Nix has copied the build results to that directory where you can examine it.

> **Note**
> 
> Check paths are not protected against garbage collection, and this path will be deleted on the next garbage collection.
> 
> The path is guaranteed to be alive for the duration of the `diff-hook`'s execution, but may be deleted any time after.
> 
> If the comparison is performed as part of automated tooling, please use the diff-hook or author your tooling to handle the case where the build was not deterministic and also a check path does not exist.

`--check` is only usable if the derivation has been built on the system already. If the derivation has not been built Nix will fail with the error:

```bash
error: some outputs of '/nix/store/hzi1h60z2qf0nb85iwnpvrai3j2w7rr6-unstable.drv'  are not valid, so checking is not possible
```

Run the build without `--check`, and then try with `--check` again.
# [Using the `post-build-hook`](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#using-the-post-build-hook)

## [Implementation Caveats](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#implementation-caveats)

Here we use the post-build hook to upload to a binary cache. This is a simple and working example, but it is not suitable for all use cases.

The post build hook program runs after each executed build, and blocks the build loop. The build loop exits if the hook program fails.

Concretely, this implementation will make Nix slow or unusable when the internet is slow or unreliable.

A more advanced implementation might pass the store paths to a user-supplied daemon or queue for processing the store paths outside of the build loop.

## [Prerequisites](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#prerequisites)

This tutorial assumes you have [configured an S3-compatible binary cache](https://nixos.org/manual/nix/unstable/package-management/s3-substituter), and that the `root` user's default AWS profile can upload to the bucket.

## [Set up a Signing Key](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#set-up-a-signing-key)

Use `nix-store --generate-binary-cache-key` to create our public and private signing keys. We will sign paths with the private key, and distribute the public key for verifying the authenticity of the paths.

```bash
# nix-store --generate-binary-cache-key example-nix-cache-1 /etc/nix/key.private /etc/nix/key.public 
# cat /etc/nix/key.public 
example-nix-cache-1:1/cKDz3QCCOmwcztD2eV6Coggp6rqc9DGjWv7C0G+rM=
```

Then update [`nix.conf`](https://nixos.org/manual/nix/unstable/command-ref/conf-file) on any machine that will access the cache. Add the cache URL to [`substituters`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-substituters) and the public key to [`trusted-public-keys`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-trusted-public-keys):

```conf
substituters = https://cache.nixos.org/ s3://example-nix-cache 
trusted-public-keys = cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY= example-nix-cache-1:1/cKDz3QCCOmwcztD2eV6Coggp6rqc9DGjWv7C0G+rM=
```

Machines that build for the cache must sign derivations using the private key. On those machines, add the path to the key file to the [`secret-key-files`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-secret-key-files) field in their [`nix.conf`](https://nixos.org/manual/nix/unstable/command-ref/conf-file):

```conf
secret-key-files = /etc/nix/key.private
```

We will restart the Nix daemon in a later step.

## [Implementing the build hook](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#implementing-the-build-hook)

Write the following script to `/etc/nix/upload-to-cache.sh`:

```sh
#!/bin/sh  

set -eu set -f # disable globbing 
export IFS=' '  

echo "Uploading paths" $OUT_PATHS 
exec nix copy --to "s3://example-nix-cache" $OUT_PATHS
```

> **Note**
> 
> The `$OUT_PATHS` variable is a space-separated list of Nix store paths. In this case, we expect and want the shell to perform word splitting to make each output path its own argument to `nix store sign`. Nix guarantees the paths will not contain any spaces, however a store path might contain glob characters. The `set -f` disables globbing in the shell. If you want to upload the `.drv` file too, the `$DRV_PATH` variable is also defined for the script and works just like `$OUT_PATHS`.

Then make sure the hook program is executable by the `root` user:

```bash
# chmod +x /etc/nix/upload-to-cache.sh
```

## [Updating Nix Configuration](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#updating-nix-configuration)

Edit `/etc/nix/nix.conf` to run our hook, by adding the following configuration snippet at the end:

```conf
post-build-hook = /etc/nix/upload-to-cache.sh
```

Then, restart the `nix-daemon`.

## [Testing](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#testing)

Build any derivation, for example:

```bash
$ nix-build --expr '(import <nixpkgs> {}).writeText "example" (builtins.toString builtins.currentTime)' this derivation will be built:   
	/nix/store/s4pnfbkalzy5qz57qs6yybna8wylkig6-example.drv 
building '/nix/store/s4pnfbkalzy5qz57qs6yybna8wylkig6-example.drv'... 
running post-build-hook '/home/grahamc/projects/github.com/NixOS/nix/post-hook.sh'... 
post-build-hook: Signing paths /nix/store/ibcyipq5gf91838ldx40mjsp0b8w9n18-example 
post-build-hook: Uploading paths /nix/store/ibcyipq5gf91838ldx40mjsp0b8w9n18-example 
/nix/store/ibcyipq5gf91838ldx40mjsp0b8w9n18-example
```

Then delete the path from the store, and try substituting it from the binary cache:

```bash
$ rm ./result 
$ nix-store --delete /nix/store/ibcyipq5gf91838ldx40mjsp0b8w9n18-example
```

Now, copy the path back from the cache:

```bash
$ nix-store --realise /nix/store/ibcyipq5gf91838ldx40mjsp0b8w9n18-example 
copying path '/nix/store/m8bmqwrch6l3h8s0k3d673xpmipcdpsa-example from 's3://example-nix-cache'... 
warning: you did not specify '--add-root'; the result might be removed by the garbage collector 
/nix/store/m8bmqwrch6l3h8s0k3d673xpmipcdpsa-example
```

## [Conclusion](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#conclusion)

We now have a Nix installation configured to automatically sign and upload every local build to a remote binary cache.

Before deploying this to production, be sure to consider the [implementation caveats](https://nixos.org/manual/nix/unstable/advanced-topics/post-build-hook#implementation-caveats).