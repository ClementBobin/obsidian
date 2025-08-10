[**home-manager**](https://nix-community.github.io/home-manager/tools.html#id-1.13.2) — reconfigure a user environment

## Name

**home-manager** — reconfigure a user environment

## Synopsis

`home-manager` { build | init [--switch] [_`dir`_] | instantiate | edit | expire-generations _`timestamp`_ | generations | help | news | option _`option.name`_ | packages | remove-generations _`ID …`_ | switch | uninstall }  
[ -A _`attrPath`_ ] [ -I _`path`_ ] [ --flake _`flake-uri`_ ] [ -b _`ext`_ ] [ { -f | --file } _`path`_ ] [ { -h | --help } ] [ --version ] [ { -n | --dry-run } ] [ --option _`name`_ _`value`_ ] [ --cores _`number`_ ] [ { -j | --max-jobs } _`number`_ ] [ --debug ] [ --impure ] [ --keep-failed ] [ --keep-going ] [ { -L | --print-build-logs } ] [ --show-trace ] [ --(no-)substitute ] [ --no-out-link ] [ --refresh ] [ { -v | --verbose } ]

## Description

This command updates the user environment so that it corresponds to the configuration specified in `$XDG_CONFIG_HOME/home-manager/home.nix` or `$XDG_CONFIG_HOME/home-manager/flake.nix`.

All operations using this tool expects a sub-command that indicates the operation to perform. It must be one of

`build`

Build configuration into a `result` directory.

`init` [`--switch`] [_`dir`_]

Generates an initial `home.nix` file for the current user. If Nix flakes are enabled, then this command also generates a `flake.nix` file.

If a path _`dir`_ is given then the configuration will be generated in that directory. Otherwise, the configuration will be generated in `~/.config/home-manager`. The output directory will be created if it does not exist.

If the `--switch` option is given, then the generated configuration is activated.

Note, this command will not overwrite any existing files. It is therefore safe to initialize a configuration, edit it, and then re-run the `init` command with `--switch` enabled to activate the configuration.

`instantiate`

Instantiate the configuration and print the resulting derivation.

`edit`

Open the home configuration using the editor indicated by `EDITOR`.

``expire-generations _`timestamp`_``

Remove generations older than _`timestamp`_ where _`timestamp`_ is interpreted as in the `-d` argument of the date(1) tool. For example `-30 days` or `2018-01-01`.

`generations`

List all home environment generations.

`help`

Print tool help.

`news`

Show news entries in a pager.

``option _`option.name`_``

Inspect the given option name in the home configuration, like nixos-option(8).

`packages`

List all packages installed in `home-manager-path`.

``remove-generations _`ID …`_``

Remove indicated generations. Use the `generations` sub-command to find suitable generation numbers.

`switch`

Build and activate the configuration.

`uninstall`

Remove Home Manager from the user environment. This will

- remove all managed files from the home directory,
    
- remove packages installed through Home Manager from the user profile, and
    
- remove all Home Manager generations and make them available for immediate garbage collection.
    

## Options

The tool accepts the options

``-A _`attrPath`_``

Optional attribute that selects a configuration expression in the configuration file. That is, if `home.nix` contains

{
  joe-at-work = {pkgs, ...}: { home.packages = [ pkgs.fortune ]; };
  joe-at-home = {pkgs, ...}: { home.packages = [ pkgs.cowsay ]; };
}

then the command **home-manager switch -A joe-at-work** will activate the profile containing the fortune program.

``-I _`path`_``

Add a path to the Nix expression search path. For example, to build a Home Manager profile using a specific Nixpkgs run **home-manager -I nixpkgs=/absolute/path/to/nixpkgs build**. By default `<nixpkgs>` is used.

``--flake _`flake-uri[#name]`_``

Build Home Manager configuration from the flake, which must contain the output homeConfigurations.name. If no name is specified it will first try username@hostname and then username.

``-b _`extension`_``

Enable automatic resolution of collisions between unmanaged and managed files. The name of the original file will be suffixed by the given extension. For example,

```
$
```

will cause a colliding file `~/.config/foo.conf` to be moved to `~/.config/foo.conf.bck`.

``-f _`path`_`` , ``--file _`path`_``

Indicates the path to the Home Manager configuration file. If not given, `$XDG_CONFIG_HOME/home-manager/home.nix` is used.

`-h` , `--help`

Prints usage information for the **home-manager** tool.

`--version`

Prints the version number of the **home-manager** tool.

`-n` , `--dry-run`

Perform a dry-run of the given operation, only prints what actions would be taken.

``--option _`name`_ _`value`_``

Passed on to nix-build(1).

``--cores _`number`_``

Passed on to nix-build(1).

``-j _`number`_`` , ``--max-jobs _`number`_``

Passed on to nix-build(1).

`--debug`

Passed on to nix-build(1).

`--impure`

Passed on to nix-build(1).

`--keep-failed`

Passed on to nix-build(1).

`--keep-going`

Passed on to nix-build(1).

`-L` , `--print-build-logs`

Passed on to nix build when building from a flake.

`--show-trace`

Passed on to nix-build(1).

`--(no-)substitute`

Passed on to nix-build(1).

`--no-out-link`

Passed on to nix-build(1) when running **home-manager build**.

`--refresh`

Passed on to nix-build(1)

`-v` , `--verbose`

Activates verbose output.

## Files

`$XDG_DATA_HOME/home-manager/news-read-ids`

Identifiers of news items that have been shown. Can be deleted to reset the read news indicator.

## Bugs

Please report any bugs on the [project issue tracker](https://github.com/nix-community/home-manager/issues).

## See also

home-configuration.nix(5)