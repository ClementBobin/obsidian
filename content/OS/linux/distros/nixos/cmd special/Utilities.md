# General
[Utilities documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities)
[Utilities documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities)
## Common options:
![[NixOS Commun store cmd#[Common Options](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed common-options)]]
## Common environment variables
![[NixOS Commun store cmd#[Common Environment Variables](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed common-environment-variables)]]
## XDG Base Directories:
![[NixOS Commun store cmd#[XDG Base Directories](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add xdg-base-directories)]]
![]()
# nix-channel
[nix-channel documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-chanel)
[nix-channel documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-channel)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#name)

`nix-channel` - manage Nix channels

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#synopsis)

```bash
nix-channel {--add url [_name_] | --remove _name_ | --list | --update [_names…_] | --list-generations | --rollback [_generation_] }
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#description)

Channels are a mechanism for referencing remote Nix expressions and conveniently retrieving their latest version.

The moving parts of channels are:

- The official channels listed at [https://nixos.org/channels](https://nixos.org/channels)
- The user-specific list of [subscribed channels](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#subscribed-channels)
- The [downloaded channel contents](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#channels)
- The [Nix expression search path](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-nix-path), set with the [`-I` option](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#opt-i) or the [`NIX_PATH` environment variable](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#env-NIX_PATH)

> **Note**
> 
> The state of a subscribed channel is external to the Nix expressions relying on it. This may limit reproducibility.
> 
> Dependencies on other Nix expressions can be declared explicitly with:
> 
> - [`fetchurl`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchurl), [`fetchTarball`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchTarball), or [`fetchGit`](https://nixos.org/manual/nix/unstable/language/builtins#builtins-fetchGit) in Nix expressions
> - the [`-I` option](https://nixos.org/manual/nix/unstable/command-ref/opt-common#opt-I) in command line invocations

This command has the following operations:

- `--add` _url_ [_name_]  
    Add a channel _name_ located at _url_ to the list of subscribed channels. If _name_ is omitted, default to the last component of _url_, with the suffixes `-stable` or `-unstable` removed.
    
    > **Note**
    > 
    > `--add` does not automatically perform an update. Use `--update` explicitly.
    
    A channel URL must point to a directory containing a file `nixexprs.tar.gz`. At the top level, that tarball must contain a single directory with a `default.nix` file that serves as the channel’s entry point.
    
- `--remove` _name_  
    Remove the channel _name_ from the list of subscribed channels.
    
- `--list`  
    Print the names and URLs of all subscribed channels on standard output.
    
- `--update` [_names_…]  
    Download the Nix expressions of subscribed channels and create a new generation. Update all channels if none is specified, and only those included in _names_ otherwise.
    
- `--list-generations`  
    Prints a list of all the current existing generations for the channel profile.
    
    Works the same way as
    
    ```bash
    nix-env --profile /nix/var/nix/profiles/per-user/$USER/channels --list-generations
    ```
    
- `--rollback` [_generation_]  
    Revert channels to the state before the last call to `nix-channel --update`. Optionally, you can specify a specific channel _generation_ number to restore.
## [Files](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#files)

`nix-channel` operates on the following files.

### [Channels](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#channels)

A directory containing symlinks to Nix channels, managed by [`nix-channel`](https://nixos.org/manual/nix/unstable/command-ref/nix-channel):

- `$XDG_STATE_HOME/nix/profiles/channels` for regular users
- `$NIX_STATE_DIR/profiles/per-user/root/channels` for `root`

[`nix-channel`](https://nixos.org/manual/nix/unstable/command-ref/nix-channel) uses a [profile](https://nixos.org/manual/nix/unstable/command-ref/files/profiles) to store channels. This profile contains symlinks to the contents of those channels.

### [Subscribed channels](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#subscribed-channels)

The list of subscribed channels is stored in

- `~/.nix-channels`
- `$XDG_STATE_HOME/nix/channels` if [`use-xdg-base-directories`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-use-xdg-base-directories) is set to `true`

in the following format:

```bash
<url> <name> 
...
```

## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-channel#examples)

Subscribe to the Nixpkgs channel and run `hello` from the GNU Hello package:

```bash
$ nix-channel --add https://nixos.org/channels/nixpkgs-unstable 
$ nix-channel --list 
nixpkgs https://nixos.org/channels/nixpkgs 
$ nix-channel --update 
$ nix-shell -p hello --run hello 
hello
```

Revert channel updates using `--rollback`:

```bash
$ nix-instantiate --eval '<nixpkgs>' --attr lib.version 
"22.11pre296212.530a53dcbc9" 

$ nix-channel --rollback 
switching from generation 483 to 482 

$ nix-instantiate --eval '<nixpkgs>' --attr 
lib.version "22.11pre281526.d0419badfad"
```

Remove a channel:

```bash
$ nix-channel --remove nixpkgs 
$ nix-channel --list
```
# nix-collect-garbage
[nix-collect-garbage documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-collect-garbage)
[nix-collect-garbage documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-collect-garbage)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#name)

`nix-collect-garbage` - delete unreachable [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object)

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#synopsis)

```bash
nix-collect-garbage [--delete-old] [-d] [--delete-older-than _period_] [--max-freed _bytes_] [--dry-run]
```
## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#description)

The command `nix-collect-garbage` is mostly an alias of [`nix-store --gc`](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc). That is, it deletes all unreachable [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object) in the Nix store to clean up your system.

However, it provides two additional options, [`--delete-old`](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#opt-delete-old) and [`--delete-older-than`](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#opt-delete-older-than), which also delete old [profiles](https://nixos.org/manual/nix/unstable/command-ref/files/profiles), allowing potentially more [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object) to be deleted because profiles are also garbage collection roots. These options are the equivalent of running [`nix-env --delete-generations`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations) with various augments on multiple profiles, prior to running `nix-collect-garbage` (or just `nix-store --gc`) without any flags.

> **Note**
> 
> Deleting previous configurations makes rollbacks to them impossible.

These flags should be used with care, because they potentially delete generations of profiles used by other users on the system.

### [Locations searched for profiles](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#locations-searched-for-profiles)

`nix-collect-garbage` cannot know about all profiles; that information doesn't exist. Instead, it looks in a few locations, and acts on all profiles it finds there:

1. The default profile locations as specified in the [profiles](https://nixos.org/manual/nix/unstable/command-ref/files/profiles) section of the manual.
    
2. > **NOTE**
    > 
    > Not stable; subject to change
    > 
    > Do not rely on this functionality; it just exists for migration purposes and is may change in the future. These deprecated paths remain a private implementation detail of Nix.
    
    `$NIX_STATE_DIR/profiles` and `$NIX_STATE_DIR/profiles/per-user`.
    
    With the exception of `$NIX_STATE_DIR/profiles/per-user/root` and `$NIX_STATE_DIR/profiles/default`, these directories are no longer used by other commands. `nix-collect-garbage` looks there anyways in order to clean up profiles from older versions of Nix.
    

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#options)

These options are for deleting old [profiles](https://nixos.org/manual/nix/unstable/command-ref/files/profiles) prior to deleting unreachable [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object).

- [`--delete-old`](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#opt-delete-old) / `-d`  
    Delete all old generations of profiles.
    
    This is the equivalent of invoking `nix-env --delete-generations old` on each found profile.
    
- [`--delete-older-than`](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#opt-delete-older-than) _period_  
    Delete all generations of profiles older than the specified amount (except for the generations that were active at that point in time). _period_ is a value such as `30d`, which would mean 30 days.
    
    This is the equivalent of invoking [`nix-env --delete-generations <period>`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#generations-time) on each found profile. See the documentation of that command for additional information about the _period_ argument.
## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-collect-garbage#example)

To delete from the Nix store everything that is not used by the current generations of each profile, do

```bash
$ nix-collect-garbage -d
```
# nix-copy-closure
[nix-copy-closure documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-copy-closure)
[nix-copy-closure documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-copy-closure)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-copy-closure#name)

`nix-copy-closure` - copy a closure to or from a remote machine via SSH

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-copy-closure#synopsis)

```bash
nix-copy-closure [--to | --from] [--gzip] [--include-outputs] [--use-substitutes | -s] [-v] _user@machine_ _paths_
```
## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-copy-closure#description)

`nix-copy-closure` gives you an easy and efficient way to exchange software between machines. Given one or more Nix store _paths_ on the local machine, `nix-copy-closure` computes the closure of those paths (i.e. all their dependencies in the Nix store), and copies all paths in the closure to the remote machine via the `ssh` (Secure Shell) command. With the `--from` option, the direction is reversed: the closure of _paths_ on a remote machine is copied to the Nix store on the local machine.

This command is efficient because it only sends the store paths that are missing on the target machine.

Since `nix-copy-closure` calls `ssh`, you may be asked to type in the appropriate password or passphrase. In fact, you may be asked _twice_ because `nix-copy-closure` currently connects twice to the remote machine, first to get the set of paths missing on the target machine, and second to send the dump of those paths. When using public key authentication, you can avoid typing the passphrase with `ssh-agent`.

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-copy-closure#options)

- `--to`  
    Copy the closure of _paths_ from the local Nix store to the Nix store on _machine_. This is the default.
    
- `--from`  
    Copy the closure of _paths_ from the Nix store on _machine_ to the local Nix store.
    
- `--gzip`  
    Enable compression of the SSH connection.
    
- `--include-outputs`  
    Also copy the outputs of [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)s included in the closure.
    
- `--use-substitutes` / `-s`  
    Attempt to download missing paths on the target machine using Nix’s substitute mechanism. Any paths that cannot be substituted on the target are still copied normally from the source. This is useful, for instance, if the connection between the source and target machine is slow, but the connection between the target machine and `nixos.org` (the default binary cache server) is fast.
    
- `-v`  
    Show verbose output.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-copy-closure#examples)

Copy Firefox with all its dependencies to a remote machine:

```bash
$ nix-copy-closure --to alice@itchy.labs $(type -tP firefox)
```

Copy Subversion from a remote machine and then install it into a user environment:

```bash
$ nix-copy-closure --from alice@itchy.labs \ 
	/nix/store/0dj0503hjxy5mbwlafv1rsbdiyx1gkdy-subversion-1.4.4 
$ nix-env --install /nix/store/0dj0503hjxy5mbwlafv1rsbdiyx1gkdy-subversion-1.4.4
```
# nix-daemon
[nix-daemon documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-daemon)
[nix-daemon documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-daemon)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-daemon#name)

`nix-daemon` - Nix multi-user support daemon

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-daemon#synopsis)

```bash
nix-daemon
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-daemon#description)

The Nix daemon is necessary in multi-user Nix installations. It runs build tasks and other operations on the Nix store on behalf of unprivileged users.
# nix-hash
[nix-hash documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-hash)
[nix-hash documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-hash)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-hash#name)

`nix-hash` - compute the cryptographic hash of a path

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-hash#synopsis)

```bash
nix-hash [--flat] [--base32] [--truncate] [--type _hashAlgo_] _path…_
```

```bash
nix-hash [--to-base16|--to-base32|--to-base64|--to-sri] [--type _hashAlgo_] _hash…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-hash#description)

The command `nix-hash` computes the cryptographic hash of the contents of each _path_ and prints it on standard output. By default, it computes an MD5 hash, but other hash algorithms are available as well. The hash is printed in hexadecimal. To generate the same hash as `nix-prefetch-url` you have to specify multiple arguments, see below for an example.

The hash is computed over a _serialisation_ of each path: a dump of the file system tree rooted at the path. This allows directories and symlinks to be hashed as well as regular files. The dump is in the _NAR format_ produced by [`nix-store --dump`](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump). Thus, `nix-hash path` yields the same cryptographic hash as `nix-store --dump path | md5sum`.

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-hash#options)

- `--flat`  
    Print the cryptographic hash of the contents of each regular file _path_. That is, do not compute the hash over the dump of _path_. The result is identical to that produced by the GNU commands `md5sum` and `sha1sum`.
    
- `--base16`  
    Print the hash in a hexadecimal representation (default).
    
- `--base32`  
    Print the hash in a base-32 representation rather than hexadecimal. This base-32 representation is more compact and can be used in Nix expressions (such as in calls to `fetchurl`).
    
- `--base64`  
    Similar to --base32, but print the hash in a base-64 representation, which is more compact than the base-32 one.
    
- `--sri`  
    Print the hash in SRI format with base-64 encoding. The type of hash algorithm will be prepended to the hash string, followed by a hyphen (-) and the base-64 hash body.
    
- `--truncate`  
    Truncate hashes longer than 160 bits (such as SHA-256) to 160 bits.
    
- `--type` _hashAlgo_  
    Use the specified cryptographic hash algorithm, which can be one of `md5`, `sha1`, `sha256`, and `sha512`.
    
- `--to-base16`  
    Don’t hash anything, but convert the base-32 hash representation _hash_ to hexadecimal.
    
- `--to-base32`  
    Don’t hash anything, but convert the hexadecimal hash representation _hash_ to base-32.
    
- `--to-base64`  
    Don’t hash anything, but convert the hexadecimal hash representation _hash_ to base-64.
    
- `--to-sri`  
    Don’t hash anything, but convert the hexadecimal hash representation _hash_ to SRI.
    
## Nix-hash info
- Nix-hash don't use the general information
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-hash#examples)

Computing the same hash as `nix-prefetch-url`:

```bash
$ nix-prefetch-url file://<(echo test) 
1lkgqb6fclns49861dwk9rzb6xnfkxbpws74mxnx01z9qyv1pjpj 
$ nix-hash --type sha256 --flat --base32 <(echo test) 
1lkgqb6fclns49861dwk9rzb6xnfkxbpws74mxnx01z9qyv1pjpj
```

Computing hashes:

```bash
$ mkdir test 
$ echo "hello" > test/world 

$ nix-hash test/ (MD5 hash; default) 
8179d3caeff1869b5ba1744e5a245c04 

$ nix-store --dump test/ | md5sum (for comparison) 
8179d3caeff1869b5ba1744e5a245c04  - 

$ nix-hash --type sha1 test/ 
e4fd8ba5f7bbeaea5ace89fe10255536cd60dab6 

$ nix-hash --type sha1 --base16 test/ 
e4fd8ba5f7bbeaea5ace89fe10255536cd60dab6 

$ nix-hash --type sha1 --base32 test/ 
nvd61k9nalji1zl9rrdfmsmvyyjqpzg4 

$ nix-hash --type sha1 --base64 test/ 
5P2Lpfe76upazon+ECVVNs1g2rY= 

$ nix-hash --type sha1 --sri test/ 
sha1-5P2Lpfe76upazon+ECVVNs1g2rY= 

$ nix-hash --type sha256 --flat test/ error: reading file `test/': Is a directory $ 
nix-hash --type sha256 --flat test/world 
5891b5b522d5df086d0ff0b110fbd9d21bb4fc7163af34d08286a2e846f6be03
```

Converting between hexadecimal, base-32, base-64, and SRI:

```bash
$ nix-hash --type sha1 --to-base32 e4fd8ba5f7bbeaea5ace89fe10255536cd60dab6 nvd61k9nalji1zl9rrdfmsmvyyjqpzg4 

$ nix-hash --type sha1 --to-base16 nvd61k9nalji1zl9rrdfmsmvyyjqpzg4 e4fd8ba5f7bbeaea5ace89fe10255536cd60dab6 

$ nix-hash --type sha1 --to-base64 e4fd8ba5f7bbeaea5ace89fe10255536cd60dab6 5P2Lpfe76upazon+ECVVNs1g2rY= 

$ nix-hash --type sha1 --to-sri nvd61k9nalji1zl9rrdfmsmvyyjqpzg4 sha1-5P2Lpfe76upazon+ECVVNs1g2rY= 

$ nix-hash --to-base16 sha1-5P2Lpfe76upazon+ECVVNs1g2rY= e4fd8ba5f7bbeaea5ace89fe10255536cd60dab6
```
# nix-instantiate
[nix-instantiate documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-instantiate)
[nix-instantiate documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-instantiate)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-instantiate#name)

`nix-instantiate` - instantiate store derivations from Nix expressions

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-instantiate#synopsis)

```bash
nix-instantiate [--parse | --eval [--strict] [--json] [--xml] ] [--read-write-mode] [--arg _name_ _value_] [{--attr| -A} _attrPath_] [--add-root _path_] [--expr | -E] _files…
```

```bash
nix-instantiate --find-file _files…
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-instantiate#description)

The command `nix-instantiate` produces [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)s from (high-level) Nix expressions. It evaluates the Nix expressions in each of _files_ (which defaults to _./default.nix_). Each top-level expression should evaluate to a derivation, a list of derivations, or a set of derivations. The paths of the resulting store derivations are printed on standard output.

If _files_ is the character `-`, then a Nix expression will be read from standard input.

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-instantiate#options)

- `--add-root` _path_  
    See the [corresponding option](https://nixos.org/manual/nix/unstable/command-ref/nix-store) in `nix-store`.
    
- `--parse`  
    Just parse the input files, and print their abstract syntax trees on standard output in ATerm format.
    
- `--eval`  
    Just parse and evaluate the input files, and print the resulting values on standard output. No instantiation of store derivations takes place.
    
- `--find-file`  
    Look up the given files in Nix’s search path (as specified by the `NIX_PATH` environment variable). If found, print the corresponding absolute paths on standard output. For instance, if `NIX_PATH` is `nixpkgs=/home/alice/nixpkgs`, then `nix-instantiate --find-file nixpkgs/default.nix` will print `/home/alice/nixpkgs/default.nix`.
    
- `--strict`  
    When used with `--eval`, recursively evaluate list elements and attributes. Normally, such sub-expressions are left unevaluated (since the Nix language is lazy).
    
    > **Warning**
    > 
    > This option can cause non-termination, because lazy data structures can be infinitely large.
    
- `--json`  
    When used with `--eval`, print the resulting value as an JSON representation of the abstract syntax tree rather than as an ATerm.
    
- `--xml`  
    When used with `--eval`, print the resulting value as an XML representation of the abstract syntax tree rather than as an ATerm. The schema is the same as that used by the [`toXML` built-in](https://nixos.org/manual/nix/unstable/language/builtins).
    
- `--read-write-mode`  
    When used with `--eval`, perform evaluation in read/write mode so nix language features that require it will still work (at the cost of needing to do instantiation of every evaluated derivation). If this option is not enabled, there may be uninstantiated store paths in the final output.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-instantiate#examples)

Instantiate [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)s from a Nix expression, and build them using `nix-store`:

```bash
$ nix-instantiate test.nix (instantiate) 
/nix/store/cigxbmvy6dzix98dxxh9b6shg7ar5bvs-perl-BerkeleyDB-0.26.drv 

$ nix-store --realise $(nix-instantiate test.nix) (build) 
... 
/nix/store/qhqk4n8ci095g3sdp93x7rgwyh9rdvgk-perl-BerkeleyDB-0.26 (output path) 

$ ls -l /nix/store/qhqk4n8ci095g3sdp93x7rgwyh9rdvgk-perl-BerkeleyDB-0.26 
dr-xr-xr-x    2 eelco    users        4096 1970-01-01 01:00 lib 
...
```

You can also give a Nix expression on the command line:

```bash
$ nix-instantiate --expr 'with import <nixpkgs> { }; hello' /nix/store/j8s4zyv75a724q38cb0r87rlczaiag4y-hello-2.8.drv
```

This is equivalent to:

```bash
$ nix-instantiate '<nixpkgs>' --attr hello
```

Parsing and evaluating Nix expressions:

```bash
$ nix-instantiate --parse --expr '1 + 2' 
1 + 2
```

```bash
$ nix-instantiate --eval --expr '1 + 2' 
3
```

```bash
$ nix-instantiate --eval --xml --expr '1 + 2' 
<?xml version='1.0' encoding='utf-8'?> 
<expr>   
	<int value="3" /> 
</expr>
```

The difference between non-strict and strict evaluation:

```bash
$ nix-instantiate --eval --xml --expr 'rec { x = "foo"; y = x; }' 
...   
<attr name="x">     
	<string value="foo" />   
</attr>   
<attr name="y">     
	<unevaluated />   
</attr> 
...
```

Note that `y` is left unevaluated (the XML representation doesn’t attempt to show non-normal forms).

```bash
$ nix-instantiate --eval --xml --strict --expr 'rec { x = "foo"; y = x; }' 
...   
<attr name="x">     
	<string value="foo" />   
</attr>   
<attr name="y">     
	<string value="foo" />   
</attr> 
...
```
# nix-prefetch-url
[nix-prefetch-url documentation stable version](https://nixos.org/manual/nix/stable/command-ref/utilities/nix-prefetch-url)
[nix-prefetch-url documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/utilities/nix-prefetch-url)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-prefetch-url#name)

`nix-prefetch-url` - copy a file from a URL into the store and print its hash

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-prefetch-url#synopsis)

```bash
nix-prefetch-url _url_ [_hash_] [--type _hashAlgo_] [--print-path] [--unpack] [--name _name_]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-prefetch-url#description)

The command `nix-prefetch-url` downloads the file referenced by the URL _url_, prints its cryptographic hash, and copies it into the Nix store. The file name in the store is `hash-baseName`, where _baseName_ is everything following the final slash in _url_.

This command is just a convenience for Nix expression writers. Often a Nix expression fetches some source distribution from the network using the `fetchurl` expression contained in Nixpkgs. However, `fetchurl` requires a cryptographic hash. If you don't know the hash, you would have to download the file first, and then `fetchurl` would download it again when you build your Nix expression. Since `fetchurl` uses the same name for the downloaded file as `nix-prefetch-url`, the redundant download can be avoided.

If _hash_ is specified, then a download is not performed if the Nix store already contains a file with the same hash and base name. Otherwise, the file is downloaded, and an error is signaled if the actual hash of the file does not match the specified hash.

This command prints the hash on standard output. The hash is printed using base-32 unless `--type md5` is specified, in which case it's printed using base-16. Additionally, if the option `--print-path` is used, the path of the downloaded file in the Nix store is also printed.

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-prefetch-url#options)

- `--type` _hashAlgo_  
    Use the specified cryptographic hash algorithm, which can be one of `md5`, `sha1`, `sha256`, and `sha512`. The default is `sha256`.
    
- `--print-path`  
    Print the store path of the downloaded file on standard output.
    
- `--unpack`  
    Unpack the archive (which must be a tarball or zip file) and add the result to the Nix store. The resulting hash can be used with functions such as Nixpkgs’s `fetchzip` or `fetchFromGitHub`.
    
- `--executable`  
    Set the executable bit on the downloaded file.
    
- `--name` _name_  
    Override the name of the file in the Nix store. By default, this is `hash-basename`, where _basename_ is the last component of _url_. Overriding the name is necessary when _basename_ contains characters that are not allowed in Nix store paths.
    

## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-prefetch-url#examples)

```bash
$ nix-prefetch-url ftp://ftp.gnu.org/pub/gnu/hello/hello-2.10.tar.gz 
0ssi1wpaf7plaswqqjwigppsg5fyh99vdlb9kzl7c9lng89ndq1i
```

```bash
$ nix-prefetch-url --print-path mirror://gnu/hello/hello-2.10.tar.gz 
0ssi1wpaf7plaswqqjwigppsg5fyh99vdlb9kzl7c9lng89ndq1i 
/nix/store/3x7dwzq014bblazs7kq20p9hyzz0qh8g-hello-2.10.tar.gz
```

```bash
$ nix-prefetch-url --unpack --print-path https://github.com/NixOS/patchelf/archive/0.8.tar.gz 
079agjlv0hrv7fxnx9ngipx14gyncbkllxrp9cccnh3a50fxcmy7 
/nix/store/19zrmhm3m40xxaw81c8cqm6aljgrnwj2-0.8.tar.gz
```