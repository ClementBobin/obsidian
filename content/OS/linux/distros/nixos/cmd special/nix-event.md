# nix-env
[nix-env documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env)
[nix-env documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env#name)

`nix-env` - manipulate or query Nix user environments

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env#synopsis)

`nix-env` _operation_ [_options_] [_arguments…_] [`--option` _name_ _value_] [`--arg` _name_ _value_] [`--argstr` _name_ _value_] [{`--file` | `-f`} _path_] [{`--profile` | `-p`} _path_] [`--system-filter` _system_] [`--dry-run`]

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env#description)

The command `nix-env` is used to manipulate Nix user environments. User environments are sets of software packages available to a user at some point in time. In other words, they are a synthesised view of the programs available in the Nix store. There may be many user environments: different users can have different environments, and individual users can switch between different environments.

`nix-env` takes exactly one _operation_ flag which indicates the subcommand to be performed. The following operations are available:

- [`--install`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install)
- [`--upgrade`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade)
- [`--uninstall`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/uninstall)
- [`--set`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set)
- [`--set-flag`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set-flag)
- [`--query`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query)
- [`--switch-profile`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-profile)
- [`--list-generations`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/list-generations)
- [`--delete-generations`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations)
- [`--switch-generation`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-generation)
- [`--rollback`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/rollback)

These pages can be viewed offline:

- `man nix-env-<operation>`.
    
    Example: `man nix-env-install`
    
- `nix-env --help --<operation>`
    
    Example: `nix-env --help --install`
    

## [Selectors](https://nixos.org/manual/nix/unstable/command-ref/nix-env#selectors)

Several commands, such as `nix-env --query` and `nix-env --install` , take a list of arguments that specify the packages on which to operate. These are extended regular expressions that must match the entire name of the package. (For details on regular expressions, see **regex**(7).) The match is case-sensitive. The regular expression can optionally be followed by a dash and a version number; if omitted, any version of the package will match. Here are some examples:

- `firefox`  
    Matches the package name `firefox` and any version.
    
- `firefox-32.0`  
    Matches the package name `firefox` and version `32.0`.
    
- `gtk\\+`  
    Matches the package name `gtk+`. The `+` character must be escaped using a backslash to prevent it from being interpreted as a quantifier, and the backslash must be escaped in turn with another backslash to ensure that the shell passes it on.
    
- `.\*`  
    Matches any package name. This is the default for most commands.
    
- `'.*zip.*'`  
    Matches any package name containing the string `zip`. Note the dots: `'*zip*'` does not work, because in a regular expression, the character `*` is interpreted as a quantifier.
    
- `'.*(firefox|chromium).*'`  
    Matches any package name containing the strings `firefox` or `chromium`.
    

## [Files](https://nixos.org/manual/nix/unstable/command-ref/nix-env#files)

`nix-env` operates on the following files.

### [Default Nix expression](https://nixos.org/manual/nix/unstable/command-ref/nix-env#default-nix-expression)

The source for the default [Nix expressions](https://nixos.org/manual/nix/unstable/language/) used by [`nix-env`](https://nixos.org/manual/nix/unstable/command-ref/nix-env):

- `~/.nix-defexpr`
- `$XDG_STATE_HOME/nix/defexpr` if [`use-xdg-base-directories`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-use-xdg-base-directories) is set to `true`.

It is loaded as follows:

- If the default expression is a file, it is loaded as a Nix expression.
- If the default expression is a directory containing a `default.nix` file, that `default.nix` file is loaded as a Nix expression.
- If the default expression is a directory without a `default.nix` file, then its contents (both files and subdirectories) are loaded as Nix expressions. The expressions are combined into a single attribute set, each expression under an attribute with the same name as the original file or subdirectory. Subdirectories without a `default.nix` file are traversed recursively in search of more Nix expressions, but the names of these intermediate directories are not added to the attribute paths of the default Nix expression.

Then, the resulting expression is interpreted like this:

- If the expression is an attribute set, it is used as the default Nix expression.
- If the expression is a function, an empty set is passed as argument and the return value is used as the default Nix expression.

For example, if the default expression contains two files, `foo.nix` and `bar.nix`, then the default Nix expression will be equivalent to

```nix
{   
	foo = import ~/.nix-defexpr/foo.nix;   
	bar = import ~/.nix-defexpr/bar.nix; 
}
```

The file [`manifest.nix`](https://nixos.org/manual/nix/unstable/command-ref/files/manifest.nix) is always ignored.

The command [`nix-channel`](https://nixos.org/manual/nix/unstable/command-ref/nix-channel) places a symlink to the user's current [channels profile](https://nixos.org/manual/nix/unstable/command-ref/files/channels) in this directory. This makes all subscribed channels available as attributes in the default expression.

### [User channel link](https://nixos.org/manual/nix/unstable/command-ref/nix-env#user-channel-link)

A symlink that ensures that [`nix-env`](https://nixos.org/manual/nix/unstable/command-ref/nix-env) can find your channels:

- `~/.nix-defexpr/channels`
- `$XDG_STATE_HOME/defexpr/channels` if [`use-xdg-base-directories`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-use-xdg-base-directories) is set to `true`.

This symlink points to:

- `$XDG_STATE_HOME/profiles/channels` for regular users
- `$NIX_STATE_DIR/profiles/per-user/root/channels` for `root`

In a multi-user installation, you may also have `~/.nix-defexpr/channels_root`, which links to the channels of the root user.[`nix-env`](https://nixos.org/manual/nix/unstable/command-ref/nix-env): ../nix-env.md

### [Profiles](https://nixos.org/manual/nix/unstable/command-ref/nix-env#profiles)

A directory that contains links to profiles managed by [`nix-env`](https://nixos.org/manual/nix/unstable/command-ref/nix-env) and [`nix profile`](https://nixos.org/manual/nix/unstable/command-ref/new-cli/nix3-profile):

- `$XDG_STATE_HOME/nix/profiles` for regular users
- `$NIX_STATE_DIR/profiles/per-user/root` if the user is `root`

A profile is a directory of symlinks to files in the Nix store.

#### [Filesystem layout](https://nixos.org/manual/nix/unstable/command-ref/nix-env#filesystem-layout)

Profiles are versioned as follows. When using a profile named _path_, _path_ is a symlink to _path_`-`_N_`-link`, where _N_ is the version of the profile. In turn, _path_`-`_N_`-link` is a symlink to a path in the Nix store. For example:

```bash
$ ls -l ~alice/.local/state/nix/profiles/profile* 
lrwxrwxrwx 1 alice users 14 Nov 25 14:35 /home/alice/.local/state/nix/profiles/profile -> profile-7-link 
lrwxrwxrwx 1 alice users 51 Oct 28 16:18 /home/alice/.local/state/nix/profiles/profile-5-link -> /nix/store/q69xad13ghpf7ir87h0b2gd28lafjj1j-profile 
lrwxrwxrwx 1 alice users 51 Oct 29 13:20 /home/alice/.local/state/nix/profiles/profile-6-link -> /nix/store/6bvhpysd7vwz7k3b0pndn7ifi5xr32dg-profile 
lrwxrwxrwx 1 alice users 51 Nov 25 14:35 /home/alice/.local/state/nix/profiles/profile-7-link -> /nix/store/mp0x6xnsg0b8qhswy6riqvimai4gm677-profile
```

Each of these symlinks is a root for the Nix garbage collector.

The contents of the store path corresponding to each version of the profile is a tree of symlinks to the files of the installed packages, e.g.

```bash
$ ll -R ~eelco/.local/state/nix/profiles/profile-7-link/ 
/home/eelco/.local/state/nix/profiles/profile-7-link/: 
total 20 
dr-xr-xr-x 2 root root 4096 Jan  1  1970 bin 
-r--r--r-- 2 root root 1402 Jan  1  1970 manifest.nix 
dr-xr-xr-x 4 root root 4096 Jan  1  1970 share  

/home/eelco/.local/state/nix/profiles/profile-7-link/bin: 
total 20 
lrwxrwxrwx 5 root root 79 Jan  1  1970 chromium -> /nix/store/ijm5k0zqisvkdwjkc77mb9qzb35xfi4m-chromium-86.0.4240.111/bin/chromium 
lrwxrwxrwx 7 root root 87 Jan  1  1970 spotify -> /nix/store/w9182874m1bl56smps3m5zjj36jhp3rn-spotify-1.1.26.501.gbe11e53b-15/bin/spotify 
lrwxrwxrwx 3 root root 79 Jan  1  1970 zoom-us -> /nix/store/wbhg2ga8f3h87s9h5k0slxk0m81m4cxl-zoom-us-5.3.469451.0927/bin/zoom-us  

/home/eelco/.local/state/nix/profiles/profile-7-link/share/applications: 
total 12 
lrwxrwxrwx 4 root root 120 Jan  1  1970 chromium-browser.desktop -> /nix/store/4cf803y4vzfm3gyk3vzhzb2327v0kl8a-chromium-unwrapped-86.0.4240.111/share/applications/chromium-browser.desktop 
lrwxrwxrwx 7 root root 110 Jan  1  1970 spotify.desktop -> /nix/store/w9182874m1bl56smps3m5zjj36jhp3rn-spotify-1.1.26.501.gbe11e53b-15/share/applications/spotify.desktop 
lrwxrwxrwx 3 root root 107 Jan  1  1970 us.zoom.Zoom.desktop -> /nix/store/wbhg2ga8f3h87s9h5k0slxk0m81m4cxl-zoom-us-5.3.469451.0927/share/applications/us.zoom.Zoom.desktop  

…
```

Each profile version contains a manifest file:

- [`manifest.nix`](https://nixos.org/manual/nix/unstable/command-ref/files/manifest.nix) used by [`nix-env`](https://nixos.org/manual/nix/unstable/command-ref/nix-env).
- [`manifest.json`](https://nixos.org/manual/nix/unstable/command-ref/files/manifest.json) used by [`nix profile`](https://nixos.org/manual/nix/unstable/command-ref/new-cli/nix3-profile) (experimental).

### [User profile link](https://nixos.org/manual/nix/unstable/command-ref/nix-env#user-profile-link)

A symbolic link to the user's current profile:

- `~/.nix-profile`
- `$XDG_STATE_HOME/nix/profile` if [`use-xdg-base-directories`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-use-xdg-base-directories) is set to `true`.

By default, this symlink points to:

- `$XDG_STATE_HOME/nix/profiles/profile` for regular users
- `$NIX_STATE_DIR/profiles/per-user/root/profile` for `root`

The `PATH` environment variable should include `/bin` subdirectory of the profile link (e.g. `~/.nix-profile/bin`) for the user environment to be visible to the user. The [installer](https://nixos.org/manual/nix/unstable/installation/installing-binary) sets this up by default, unless you enable [`use-xdg-base-directories`](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-use-xdg-base-directories).

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#options)

The following options are allowed for all `nix-env` operations, but may not always have an effect.

- `--file` / `-f` _path_  
    Specifies the Nix expression (designated below as the _active Nix expression_) used by the `--install`, `--upgrade`, and `--query --available` operations to obtain derivations. The default is `~/.nix-defexpr`.
    
    If the argument starts with `http://` or `https://`, it is interpreted as the URL of a tarball that will be downloaded and unpacked to a temporary location. The tarball must include a single top-level directory containing at least a file named `default.nix`.
    
- `--profile` / `-p` _path_  
    Specifies the profile to be used by those operations that operate on a profile (designated below as the _active profile_). A profile is a sequence of user environments called _generations_, one of which is the _current generation_.
    
- `--dry-run`  
    For the `--install`, `--upgrade`, `--uninstall`, `--switch-generation`, `--delete-generations` and `--rollback` operations, this flag will cause `nix-env` to print what _would_ be done if this flag had not been specified, without actually doing it.
    
    `--dry-run` also prints out which paths will be [substituted](https://nixos.org/manual/nix/unstable/glossary) (i.e., downloaded) and which paths will be built from source (because no substitute is available).
    
- `--system-filter` _system_  
    By default, operations such as `--query --available` show derivations matching any platform. This option allows you to use derivations for the specified platform _system_.
## Common Options
![[NixOS Commun store cmd#[Common Options](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed common-options)]]
## XDG Base Directories
![[NixOS Commun store cmd#[XDG Base Directories](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add xdg-base-directories)]]
![]()
## [Environment variables](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#environment-variables)

- `NIX_PROFILE`  
    Location of the Nix profile. Defaults to the target of the symlink `~/.nix-profile`, if it exists, or `/nix/var/nix/profiles/default` otherwise.
## Common Environment Variables
![[NixOS Commun store cmd#[Common Environment Variables](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed common-environment-variables)]]
[]()
# nix-env --delete-generations
[nix-env --delete-generations documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/delete-generations)
[nix-env -- delete-generations documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#name)

`nix-env --delete-generations` - delete profile generations

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#synopsis)

```bash
nix-env --delete-generations _generations_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#description)

This operation deletes the specified generations of the current profile.

_generations_ can be a one of the following:

- `<number>...`:  
    A list of generation numbers, each one a separate command-line argument.
    
    Delete exactly the profile generations given by their generation number. Deleting the current generation is not allowed.
    
- The special value `old`
    
    Delete all generations except the current one.
    
    > **WARNING**
    > 
    > Older _and newer_ generations will be deleted by this operation.
    > 
    > One might expect this to just delete older generations than the curent one, but that is only true if the current generation is also the latest. Because one can roll back to a previous generation, it is possible to have generations newer than the current one. They will also be deleted.
    
- `<number>d`:  
    The last _number_ days
    
    _Example_: `30d`
    
    Delete all generations created more than _number_ days ago, except the most recent one of them. This allows rolling back to generations that were available within the specified period.
    
- `+<number>`:  
    The last _number_ generations up to the present
    
    _Example_: `+5`
    
    Keep the last _number_ generations, along with any newer than current.
    

Periodically deleting old generations is important to make garbage collection effective. The is because profiles are also garbage collection roots — any [store object](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object) reachable from a profile is "alive" and ineligible for deletion.

## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#examples)

## [Delete explicit generation numbers](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#delete-explicit-generation-numbers)

```bash
$ nix-env --delete-generations 3 4 8
```
Delete the generations numbered 3, 4, and 8, so long as the current active generation is not any of those.

## [Keep most-recent by count (number of generations)](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#keep-most-recent-by-count-number-of-generations)

```bash
$ nix-env --delete-generations +5
```

Suppose `30` is the current generation, and we currently have generations numbered `20` through `32`.

Then this command will delete generations `20` through `25` (`<= 30 - 5`), and keep generations `26` through `31` (`> 30 - 5`).

## [Keep most-recent by time (number of days)](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#keep-most-recent-by-time-number-of-days)

```bash
$ nix-env --delete-generations 30d
```

This command will delete all generations older than 30 days, except for the generation that was active 30 days ago (if it currently exists).

## [Delete all older](https://nixos.org/manual/nix/unstable/command-ref/nix-env/delete-generations#delete-all-older)

```bash
$ nix-env --profile other_profile --delete-generations old
```
# nix-env --install
[nix-env --install documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/install)
[nix-env --install documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install#name)

`nix-env --install` - add packages to user environment

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install#synopsis)

```bash
nix-env {--install | -i} _args…_ [{--prebuilt-only | -b}] [{--attr | -A}] [--from-expression] [-E] [--from-profile _path_] [--preserve-installed | -P] [--remove-all | -r]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install#description)

The install operation creates a new user environment. It is based on the current generation of the active [profile](https://nixos.org/manual/nix/unstable/command-ref/files/profiles), to which a set of [store paths](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) described by _args_ is added.

The arguments _args_ map to store paths in a number of possible ways:

- By default, _args_ is a set of [derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-derivation) names denoting derivations in the [default Nix expression](https://nixos.org/manual/nix/unstable/command-ref/files/default-nix-expression). These are [realised](https://nixos.org/manual/nix/unstable/glossary#gloss-realise), and the resulting output paths are installed. Currently installed derivations with a name equal to the name of a derivation being added are removed unless the option `--preserve-installed` is specified.
    
    If there are multiple derivations matching a name in _args_ that have the same name (e.g., `gcc-3.3.6` and `gcc-4.1.1`), then the derivation with the highest _priority_ is used. A derivation can define a priority by declaring the `meta.priority` attribute. This attribute should be a number, with a higher value denoting a lower priority. The default priority is `5`.
    
    If there are multiple matching derivations with the same priority, then the derivation with the highest version will be installed.
    
    You can force the installation of multiple derivations with the same name by being specific about the versions. For instance, `nix-env --install gcc-3.3.6 gcc-4.1.1` will install both version of GCC (and will probably cause a user environment conflict!).
    
- If [`--attr`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install#opt-attr) / `-A` is specified, the arguments are _attribute paths_ that select attributes from the [default Nix expression](https://nixos.org/manual/nix/unstable/command-ref/files/default-nix-expression). This is faster than using derivation names and unambiguous. Show the attribute paths of available packages with [`nix-env --query`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query):
    
    ```bash
     nix-env --query --available --attr-path
    ```
    
- If `--from-profile` _path_ is given, _args_ is a set of names denoting installed [store paths](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) in the profile _path_. This is an easy way to copy user environment elements from one profile to another.
    
- If `--from-expression` is given, _args_ are [Nix language functions](https://nixos.org/manual/nix/unstable/language/constructs#functions) that are called with the [default Nix expression](https://nixos.org/manual/nix/unstable/command-ref/files/default-nix-expression) as their single argument. The derivations returned by those function calls are installed. This allows derivations to be specified in an unambiguous way, which is necessary if there are multiple derivations with the same name.
    
- If _args_ are [store derivations](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation), then these are [realised](https://nixos.org/manual/nix/unstable/glossary#gloss-realise), and the resulting output paths are installed.
    
- If _args_ are [store paths](https://nixos.org/manual/nix/unstable/glossary#gloss-store-path) that are not store derivations, then these are [realised](https://nixos.org/manual/nix/unstable/glossary#gloss-realise) and installed.
    
- By default all [outputs](https://nixos.org/manual/nix/unstable/language/derivations#attr-outputs) are installed for each [derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-derivation). This can be overridden by adding a `meta.outputsToInstall` attribute on the derivation listing a subset of the output names.
    
    Example:
    
    The file `example.nix` defines a derivation with two outputs `foo` and `bar`, each containing a file.
    
    ```nix
    # example.nix 
    
    let   
	    pkgs = import <nixpkgs> {};   
	    command = ''     
		    ${pkgs.coreutils}/bin/mkdir -p $foo $bar     
		    echo foo > $foo/foo-file     
		    echo bar > $bar/bar-file   
	    ''; 
	in 
		derivation {   
			name = "example";   
			builder = "${pkgs.bash}/bin/bash";   
			args = [ "-c" command ];   
			outputs = [ "foo" "bar" ];   
			system = builtins.currentSystem; 
		}
    ```
    
    Installing from this Nix expression will make files from both outputs appear in the current profile.
    
    ```bash
    $ nix-env --install --file example.nix 
    installing 'example' 
    $ ls ~/.nix-profile 
    foo-file 
    bar-file 
    manifest.nix
    ```
    
    Adding `meta.outputsToInstall` to that derivation will make `nix-env` only install files from the specified outputs.
    
    ```nix
    # example-outputs.nix 
    import ./example.nix // { meta.outputsToInstall = [ "bar" ]; }
    ```
    
    ```nix
    $ nix-env --install --file example-outputs.nix 
    installing 'example' 
    $ ls ~/.nix-profile 
    bar-file 
    manifest.nix
    ```
    

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install#options)

- `--prebuilt-only` / `-b`
    
    Use only derivations for which a substitute is registered, i.e., there is a pre-built binary available that can be downloaded in lieu of building the derivation. Thus, no packages will be built from source.
    
- `--preserve-installed` / `-P`
    
    Do not remove derivations with a name matching one of the derivations being installed. Usually, trying to have two versions of the same package installed in the same generation of a profile will lead to an error in building the generation, due to file name clashes between the two versions. However, this is not the case for all packages.
    
- `--remove-all` / `-r`
    
    Remove all previously installed packages first. This is equivalent to running `nix-env --uninstall '.*'` first, except that everything happens in a single transaction.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/install#examples)

To install a package using a specific attribute path from the active Nix expression:

```bash
$ nix-env --install --attr gcc40mips 
installing `gcc-4.0.2' 
$ nix-env --install --attr xorg.xorgserver 
installing `xorg-server-1.2.0'
```

To install a specific version of `gcc` using the derivation name:

```bash
$ nix-env --install gcc-3.3.2 
installing `gcc-3.3.2' 
uninstalling `gcc-3.1'
```

Using attribute path for selecting a package is preferred, as it is much faster and there will not be multiple matches.

Note the previously installed version is removed, since `--preserve-installed` was not specified.

To install an arbitrary version:

```bash
$ nix-env --install gcc 
installing `gcc-3.3.2'
```

To install all derivations in the Nix expression `foo.nix`:

```bash
$ nix-env --file ~/foo.nix --install '.*'
```

To copy the store path with symbolic name `gcc` from another profile:

```bash
$ nix-env --install --from-profile /nix/var/nix/profiles/foo gcc
```

To install a specific [store derivation] (typically created by `nix-instantiate`):

```bash
$ nix-env --install /nix/store/fibjb1bfbpm5mrsxc4mh2d8n37sxh91i-gcc-3.4.3.drv
```

To install a specific output path:

```bash
$ nix-env --install /nix/store/y3cgx0xj1p4iv9x0pnnmdhr8iyg741vk-gcc-3.4.3
```

To install from a Nix expression specified on the command-line:

```bash
$ nix-env --file ./foo.nix --install --expr \     
	'f: (f {system = "i686-linux";}).subversionWithJava'
```

I.e., this evaluates to `(f: (f {system = "i686-linux";}).subversionWithJava) (import ./foo.nix)`, thus selecting the `subversionWithJava` attribute from the set returned by calling the function defined in `./foo.nix`.

A dry-run tells you which paths will be downloaded or built from source:

```bash
$ nix-env --file '<nixpkgs>' --install --attr hello --dry-run 
(dry run; not doing anything) 
installing ‘hello-2.10’ 
this path will be fetched (0.04 MiB download, 0.19 MiB unpacked):   
	/nix/store/wkhdf9jinag5750mqlax6z2zbwhqb76n-hello-2.10   
	...
```

To install Firefox from the latest revision in the Nixpkgs/NixOS 14.12 channel:

```bash
$ nix-env --file https://github.com/NixOS/nixpkgs/archive/nixos-14.12.tar.gz --install --attr firefox
```
# nix-env --list-generations
[nix-env --list-generations documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/list-generations)
[nix-env --list-generations documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/list-generations)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/list-generations#name)

`nix-env --list-generations` - list profile generations

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/list-generations#synopsis)

```bash
nix-env --list-generations
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/list-generations#description)

This operation print a list of all the currently existing generations for the active profile. These may be switched to using the `--switch-generation` operation. It also prints the creation date of the generation, and indicates the current generation.

## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/list-generations#examples)

```bash
$ nix-env --list-generations   
95   2004-02-06 11:48:24   
96   2004-02-06 11:49:01   
97   2004-02-06 16:22:45   
98   2004-02-06 16:24:33   (current)
```

# nix-env --query
[nix-env --query documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/query)
[nix-env --query documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query#name)

`nix-env --query` - display information about packages

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query#synopsis)

```bash
nix-env {--query | -q} _names…_ [--installed | --available | -a] [{--status | -s}] [{--attr-path | -P}] [--no-name] [{--compare-versions | -c}] [--system] [--drv-path] [--out-path] [--description] [--meta] [--xml] [--json] [{--prebuilt-only | -b}] [{--attr | -A} _attribute-path_]
```
## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query#description)

The query operation displays information about either the store paths that are installed in the current generation of the active profile (`--installed`), or the derivations that are available for installation in the active Nix expression (`--available`). It only prints information about derivations whose symbolic name matches one of _names_.

The derivations are sorted by their `name` attributes.

## [Source selection](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query#source-selection)

The following flags specify the set of things on which the query operates.

- `--installed`  
    The query operates on the store paths that are installed in the current generation of the active profile. This is the default.
    
- `--available`; `-a`  
    The query operates on the derivations that are available in the active Nix expression.
    

## [Queries](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query#queries)

The following flags specify what information to display about the selected derivations. Multiple flags may be specified, in which case the information is shown in the order given here. Note that the name of the derivation is shown unless `--no-name` is specified.

- `--xml`  
    Print the result in an XML representation suitable for automatic processing by other tools. The root element is called `items`, which contains a `item` element for each available or installed derivation. The fields discussed below are all stored in attributes of the `item` elements.
    
- `--json`  
    Print the result in a JSON representation suitable for automatic processing by other tools.
    
- `--prebuilt-only` / `-b`  
    Show only derivations for which a substitute is registered, i.e., there is a pre-built binary available that can be downloaded in lieu of building the derivation. Thus, this shows all packages that probably can be installed quickly.
    
- `--status`; `-s`  
    Print the _status_ of the derivation. The status consists of three characters. The first is `I` or `-`, indicating whether the derivation is currently installed in the current generation of the active profile. This is by definition the case for `--installed`, but not for `--available`. The second is `P` or `-`, indicating whether the derivation is present on the system. This indicates whether installation of an available derivation will require the derivation to be built. The third is `S` or `-`, indicating whether a substitute is available for the derivation.
    
- `--attr-path`; `-P`  
    Print the _attribute path_ of the derivation, which can be used to unambiguously select it using the `--attr` option available in commands that install derivations like `nix-env --install`. This option only works together with `--available`
    
- `--no-name`  
    Suppress printing of the `name` attribute of each derivation.
    
- `--compare-versions` / `-c`  
    Compare installed versions to available versions, or vice versa (if `--available` is given). This is useful for quickly seeing whether upgrades for installed packages are available in a Nix expression. A column is added with the following meaning:
    
    - `<` _version_  
        A newer version of the package is available or installed.
        
    - `=` _version_  
        At most the same version of the package is available or installed.
        
    - `>` _version_  
        Only older versions of the package are available or installed.
        
    - `- ?`  
        No version of the package is available or installed.
        
- `--system`  
    Print the `system` attribute of the derivation.
    
- `--drv-path`  
    Print the path of the [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation).
    
- `--out-path`  
    Print the output path of the derivation.
    
- `--description`  
    Print a short (one-line) description of the derivation, if available. The description is taken from the `meta.description` attribute of the derivation.
    
- `--meta`  
    Print all of the meta-attributes of the derivation. This option is only available with `--xml` or `--json`.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/query#examples)

To show installed packages:

```bash
$ nix-env --query 
bison-1.875c 
docbook-xml-4.2 
firefox-1.0.4 
MPlayer-1.0pre7 
ORBit2-2.8.3 
…
```

To show available packages:

```bash
$ nix-env --query --available 
firefox-1.0.7 
GConf-2.4.0.1 
MPlayer-1.0pre7 
ORBit2-2.8.3 
…
```

To show the status of available packages:

```bash
$ nix-env --query --available --status 
-P- firefox-1.0.7   (not installed but present) 
--S GConf-2.4.0.1   (not present, but there is a substitute for fast installation) 
--S MPlayer-1.0pre3 (i.e., this is not the installed MPlayer, even though the version is the same!) 
IP- ORBit2-2.8.3    (installed and by definition present) 
…
```

To show available packages in the Nix expression `foo.nix`:

```bash
$ nix-env --file ./foo.nix --query --available 
foo-1.2.3
```

To compare installed versions to what’s available:

```bash
$ nix-env --query --compare-versions 
... 
acrobat-reader-7.0 - ?      (package is not available at all) 
autoconf-2.59      = 2.59   (same version) 
firefox-1.0.4      < 1.0.7  (a more recent version is available) 
...
```

To show all packages with “`zip`” in the name:

```bash
$ nix-env --query --available '.*zip.*' 
bzip2-1.0.6 
gzip-1.6 
zip-3.0 
…
```

To show all packages with “`firefox`” or “`chromium`” in the name:

```bash
$ nix-env --query --available '.*(firefox|chromium).*' 
chromium-37.0.2062.94 
chromium-beta-38.0.2125.24 
firefox-32.0.3 
firefox-with-plugins-13.0.1 
…
```

To show all packages in the latest revision of the Nixpkgs repository:

```bash
$ nix-env --file https://github.com/NixOS/nixpkgs/archive/master.tar.gz --query --available
```
# nix-event --rollback
[nix-env --rollback documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/rollback)
[nix-env --rollback documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/rollback)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/rollback#name)

`nix-env --rollback` - set user environment to previous generation

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/rollback#synopsis)

```bash
nix-env --rollback
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/rollback#description)

This operation switches to the “previous” generation of the active profile, that is, the highest numbered generation lower than the current generation, if it exists. It is just a convenience wrapper around `--list-generations` and `--switch-generation`.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/rollback#examples)

```bash
$ nix-env --rollback 
switching from generation 92 to 91
```

```bash
$ nix-env --rollback 
error: no generation older than the current (91) exists
```
# nix-event --set-flag
[nix-env --set-flag documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/set-flag)
[nix-env --set-flag documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set-flag)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set-flag#name)

`nix-env --set-flag` - modify meta attributes of installed packages

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set-flag#synopsis)

```bash
nix-env --set-flag _name_ _value_ _drvnames_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set-flag#description)

The `--set-flag` operation allows meta attributes of installed packages to be modified. There are several attributes that can be usefully modified, because they affect the behaviour of `nix-env` or the user environment build script:

- `priority` can be changed to resolve filename clashes. The user environment build script uses the `meta.priority` attribute of derivations to resolve filename collisions between packages. Lower priority values denote a higher priority. For instance, the GCC wrapper package and the Binutils package in Nixpkgs both have a file `bin/ld`, so previously if you tried to install both you would get a collision. Now, on the other hand, the GCC wrapper declares a higher priority than Binutils, so the former’s `bin/ld` is symlinked in the user environment.
    
- `keep` can be set to `true` to prevent the package from being upgraded or replaced. This is useful if you want to hang on to an older version of a package.
    
- `active` can be set to `false` to “disable” the package. That is, no symlinks will be generated to the files of the package, but it remains part of the profile (so it won’t be garbage-collected). It can be set back to `true` to re-enable the package.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set-flag#examples)

To prevent the currently installed Firefox from being upgraded:

```bash
$ nix-env --set-flag keep true firefox
```

After this, `nix-env --upgrade` will ignore Firefox.

To disable the currently installed Firefox, then install a new Firefox while the old remains part of the profile:

```bash
$ nix-env --query 
firefox-2.0.0.9 (the current one) 

$ nix-env --preserve-installed --install firefox-2.0.0.11 
installing `firefox-2.0.0.11' 
building path(s) `/nix/store/myy0y59q3ig70dgq37jqwg1j0rsapzsl-user-environment' 
collision between `/nix/store/...-firefox-2.0.0.11/bin/firefox'   
	and `/nix/store/...-firefox-2.0.0.9/bin/firefox'. 
(i.e., can’t have two active at the same time) 

$ nix-env --set-flag active false firefox 
setting flag on `firefox-2.0.0.9' 

$ nix-env --preserve-installed --install firefox-2.0.0.11 
installing `firefox-2.0.0.11' 

$ nix-env --query 
firefox-2.0.0.11 (the enabled one) 
firefox-2.0.0.9 (the disabled one)
```

To make files from `binutils` take precedence over files from `gcc`:

```bash
$ nix-env --set-flag priority 5 binutils 
$ nix-env --set-flag priority 10 gcc
```
# nix-event --set
[nix-env --set documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/set)
[nix-env --set documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set#name)

`nix-env --set` - set profile to contain a specified derivation

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set#synopsis)

```bash
nix-env --set _drvname_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set#description)

The `--set` operation modifies the current generation of a profile so that it contains exactly the specified derivation, and nothing else.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/set#examples)

The following updates a profile such that its current generation will contain just Firefox:

```bash
$ nix-env --profile /nix/var/nix/profiles/browser --set firefox
```
# nix-env --switch-generation
[nix-env --switch-generation documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/switch-generation)
[nix-env --switch-generation documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-generation)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-generation#name)

`nix-env --switch-generation` - set user environment to given profile generation

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-generation#synopsis)

```bash
nix-env {--switch-generation | -G} _generation_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-generation#description)

This operation makes generation number _generation_ the current generation of the active profile. That is, if the `profile` is the path to the active profile, then the symlink `profile` is made to point to `profile-generation-link`, which is in turn a symlink to the actual user environment in the Nix store.

Switching will fail if the specified generation does not exist.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-generation#examples)

```bash
$ nix-env --switch-generation 
42 switching from generation 50 to 42
```
# nix-env --switch-profile
[nix-env --switch-profile documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/switch-profile)
[nix-env --switch-profile documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-profile)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-profile#name)

`nix-env --switch-profile` - set user environment to given profile

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-profile#synopsis)

```bash
nix-env {--switch-profile | -S} _path_
```
## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-profile#description)

This operation makes _path_ the current profile for the user. That is, the symlink `~/.nix-profile` is made to point to _path_.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/switch-profile#examples)

```bash
$ nix-env --switch-profile ~/my-profile
```
# nix-env --uninstall
[nix-env --uninstall documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/uninstall)
[nix-env --uninstall documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/uninstall)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/uninstall#name)

`nix-env --uninstall` - remove packages from user environment

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/uninstall#synopsis)

```bash
nix-env {--uninstall | -e} _drvnames…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/uninstall#description)

The uninstall operation creates a new user environment, based on the current generation of the active profile, from which the store paths designated by the symbolic names _drvnames_ are removed.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/uninstall#examples)

```bash
$ nix-env --uninstall gcc 
$ nix-env --uninstall '.*' (remove everything)
```
# nix-env --upgrade
[nix-env --upgrade documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-env/upgrade)
[nix-env --upgrade documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#name)

`nix-env --upgrade` - upgrade packages in user environment

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#synopsis)

```bash
nix-env {--upgrade | -u} _args_ [--lt | --leq | --eq | --always] [{--prebuilt-only | -b}] [{--attr | -A}] [--from-expression] [-E] [--from-profile`_path_] [--preserve-installed | -P]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#description)

The upgrade operation creates a new user environment, based on the current generation of the active profile, in which all store paths are replaced for which there are newer versions in the set of paths described by _args_. Paths for which there are no newer versions are left untouched; this is not an error. It is also not an error if an element of _args_ matches no installed derivations.

For a description of how _args_ is mapped to a set of store paths, see [`--install`](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#operation---install). If _args_ describes multiple store paths with the same symbolic name, only the one with the highest version is installed.

## [Flags](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#flags)

- `--lt`  
    Only upgrade a derivation to newer versions. This is the default.
    
- `--leq`  
    In addition to upgrading to newer versions, also “upgrade” to derivations that have the same version. Version are not a unique identification of a derivation, so there may be many derivations that have the same version. This flag may be useful to force “synchronisation” between the installed and available derivations.
    
- `--eq`  
    _Only_ “upgrade” to derivations that have the same version. This may not seem very useful, but it actually is, e.g., when there is a new release of Nixpkgs and you want to replace installed applications with the same versions built against newer dependencies (to reduce the number of dependencies floating around on your system).
    
- `--always`  
    In addition to upgrading to newer versions, also “upgrade” to derivations that have the same or a lower version. I.e., derivations may actually be downgraded depending on what is available in the active Nix expression.
    
- `--prebuilt-only` / `-b`  
    Use only derivations for which a substitute is registered, i.e., there is a pre-built binary available that can be downloaded in lieu of building the derivation. Thus, no packages will be built from source.
    
- `--preserve-installed` / `-P`  
    Do not remove derivations with a name matching one of the derivations being installed. Usually, trying to have two versions of the same package installed in the same generation of a profile will lead to an error in building the generation, due to file name clashes between the two versions. However, this is not the case for all packages.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#examples)

```bash
$ nix-env --upgrade --attr nixpkgs.gcc 
upgrading `gcc-3.3.1' to `gcc-3.4'
```

When there are no updates available, nothing will happen:

```bash
$ nix-env --upgrade --attr nixpkgs.pan
```

Using `-A` is preferred when possible, as it is faster and unambiguous but it is also possible to upgrade to a specific version by matching the derivation name:

```bash
$ nix-env --upgrade gcc-3.3.2 --always 
upgrading `gcc-3.4' to `gcc-3.3.2'
```

To try to upgrade everything (matching packages based on the part of the derivation name without version):

```bash
$ nix-env --upgrade 
upgrading `hello-2.1.2' to `hello-2.1.3' 
upgrading `mozilla-1.2' to `mozilla-1.4'
```

## [Versions](https://nixos.org/manual/nix/unstable/command-ref/nix-env/upgrade#versions)

The upgrade operation determines whether a derivation `y` is an upgrade of a derivation `x` by looking at their respective `name` attributes. The names (e.g., `gcc-3.3.1` are split into two parts: the package name (`gcc`), and the version (`3.3.1`). The version part starts after the first dash not followed by a letter. `y` is considered an upgrade of `x` if their package names match, and the version of `y` is higher than that of `x`.

The versions are compared by splitting them into contiguous components of numbers and letters. E.g., `3.3.1pre5` is split into `[3, 3, 1, "pre", 5]`. These lists are then compared lexicographically (from left to right). Corresponding components `a` and `b` are compared as follows. If they are both numbers, integer comparison is used. If `a` is an empty string and `b` is a number, `a` is considered less than `b`. The special string component `pre` (for _pre-release_) is considered to be less than other components. String components are considered less than number components. Otherwise, they are compared lexicographically (i.e., using case-sensitive string comparison).

This is illustrated by the following examples:

```bash
1.0 < 2.3 
2.1 < 2.3 
2.3 = 2.3 
2.5 > 2.3 
3.1 > 2.3 
2.3.1 > 2.3 
2.3.1 > 2.3a 
2.3pre1 < 2.3 
2.3pre3 < 2.3pre12 
2.3a < 2.3c 
2.3pre1 < 2.3c 
2.3pre1 < 2.3q
```