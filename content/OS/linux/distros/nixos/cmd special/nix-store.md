[nix-store documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store)
[nix-store documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store)
# nix-store general
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store#name)

`nix-store` - manipulate or query the Nix store

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store#synopsis)

```bash
nix-store _operation_ [_options…_] [_arguments…_] [--option _name_ _value_] [--add-root _path_]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store#description)

The command `nix-store` performs primitive operations on the Nix store. You generally do not need to run this command manually.

`nix-store` takes exactly one _operation_ flag which indicates the subcommand to be performed. The following operations are available:

- [`--realise`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--realise)
- [`--serve`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--serve)
- [`--gc`](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc)
- [`--delete`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--delete)
- [`--query`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--query)
- [`--add`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--add)
- [`--add-fixed`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--add-fixed)
- [`--verify`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--verify)
- [`--verify-path`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--verify-path)
- [`--repair-path`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--repair-app)
- [`--dump`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--dump)
- [`--restore`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--restore)
- [`--export`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--export)
- [`--import`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--import)
- [`--optimise`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--optimise)
- [`--read-log`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--read-log)
- [`--dump-db`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--dump-db)
- [`--load-db`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--load-dp)
- [`--print-env`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--print-env)
- [`--generate-binary-cache-key`](OS/linux/distros/nixos/cmd%20special/nix-store#nix-store%20--generate-binary-cache-key)

These pages can be viewed offline:

- `man nix-store-<operation>`
    
    Example: `man nix-store-realise`
    
- `nix-store --help --<operation>`
    
    Example: `nix-store --help --realise`
## Options

![[NixOS Commun store cmd#[Options](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed options)]]
## Common Options
![[NixOS Commun store cmd#[Common Options](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed common-options)]]
## XDG Base Directories
![[NixOS Commun store cmd#[XDG Base Directories](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add xdg-base-directories)]]

## Common Environment Variables
![[NixOS Commun store cmd#[Common Environment Variables](https //nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed common-environment-variables)]]
()
[]()
# nix-store --add-fixed
[nix-store --add-fixed documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/add-fixed)
[nix-store --add-fixed documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed#name)

`nix-store --add-fixed` - add paths to store using given hashing algorithm

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed#synopsis)

```bash
nix-store --add-fixed [`--recursive`] _algorithm_ _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed#description)

The operation `--add-fixed` adds the specified paths to the Nix store. Unlike `--add` paths are registered using the specified hashing algorithm, resulting in the same output path as a fixed-output derivation. This can be used for sources that are not available from a public url or broke since the download expression was written.

This operation has the following options:

- `--recursive`  
    Use recursive instead of flat hashing mode, used when adding directories to the store.

## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add-fixed#example)

```bash
$ nix-store --add-fixed sha256 ./hello-2.10.tar.gz /nix/store/3x7dwzq014bblazs7kq20p9hyzz0qh8g-hello-2.10.tar.gz
```

# nix-store --add
[nix-store --add documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/add)
[nix-store --add documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add#name)

`nix-store --add` - add paths to Nix store

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add#synopsis)

```bash
nix-store --add _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add#description)

The operation `--add` adds the specified paths to the Nix store. It prints the resulting paths in the Nix store on standard output.

## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/add#example)

```bash
$ nix-store --add ./foo.c /nix/store/m7lrha58ph6rcnv109yzx1nk1cj7k7zf-foo.c
```
# nix-store --delete
[nix-store --delete documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/delete)
[nix-store --delete documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/delete)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/delete#name)

`nix-store --delete` - delete store paths

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/delete#synopsis)

```bash
nix-store --delete [`--ignore-liveness`] _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/delete#description)

The operation `--delete` deletes the store paths _paths_ from the Nix store, but only if it is safe to do so; that is, when the path is not reachable from a root of the garbage collector. This means that you can only delete paths that would also be deleted by `nix-store --gc`. Thus, `--delete` is a more targeted version of `--gc`.

With the option `--ignore-liveness`, reachability from the roots is ignored. However, the path still won’t be deleted if there are other paths in the store that refer to it (i.e., depend on it).

## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/delete#example)

```bash
$ nix-store --delete /nix/store/zq0h41l75vlb4z45kzgjjmsjxvcv1qk7-mesa-6.4 
0 bytes freed (0.00 MiB) 
error: cannot delete path `/nix/store/zq0h41l75vlb4z45kzgjjmsjxvcv1qk7-mesa-6.4' since it is still alive
```
# nix-store --dump-db [_paths…_]
[nix-store --dump-db documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/dump-db)
[nix-store --dump-db documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump-db)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump-db#name)

`nix-store --dump-db` - export Nix database

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump-db#synopsis)

```bash
nix-store --dump-db [_paths…_]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump-db#description)

The operation `--dump-db` writes a dump of the Nix database to standard output. It can be loaded into an empty Nix store using `--load-db`. This is useful for making backups and when migrating to different database schemas.

By default, `--dump-db` will dump the entire Nix database. When one or more store paths is passed, only the subset of the Nix database for those store paths is dumped. As with `--export`, the user is responsible for passing all the store paths for a closure. See `--export` for an example.
# nix-store --dump
[nix-store --dump documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/dump)
[nix-store --dump documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump#name)

`nix-store --dump` - write a single path to a Nix Archive

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump#synopsis)

```bash
nix-store --dump _path_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/dump#description)

The operation `--dump` produces a NAR (Nix ARchive) file containing the contents of the file system tree rooted at _path_. The archive is written to standard output.

A NAR archive is like a TAR or Zip archive, but it contains only the information that Nix considers important. For instance, timestamps are elided because all files in the Nix store have their timestamp set to 0 anyway. Likewise, all permissions are left out except for the execute bit, because all files in the Nix store have 444 or 555 permission.

Also, a NAR archive is _canonical_, meaning that “equal” paths always produce the same NAR archive. For instance, directory entries are always sorted so that the actual on-disk order doesn’t influence the result. This means that the cryptographic hash of a NAR dump of a path is usable as a fingerprint of the contents of the path. Indeed, the hashes of store paths stored in Nix’s database (see `nix-store --query --hash`) are SHA-256 hashes of the NAR dump of each store path.

NAR archives support filenames of unlimited length and 64-bit file sizes. They can contain regular files, directories, and symbolic links, but not other types of files (such as device nodes).

A Nix archive can be unpacked using `nix-store --restore`.
# nix-store --export
[nix-store --export documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/export)
[nix-store --export documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/export)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/export#name)

`nix-store --export` - export store paths to a Nix Archive

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/export#synopsis)

```bash
nix-store --export _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/export#description)

The operation `--export` writes a serialisation of the specified store paths to standard output in a format that can be imported into another Nix store with `nix-store --import`. This is like `nix-store --dump`, except that the NAR archive produced by that command doesn’t contain the necessary meta-information to allow it to be imported into another Nix store (namely, the set of references of the path).

This command does not produce a _closure_ of the specified paths, so if a store path references other store paths that are missing in the target Nix store, the import will fail.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-store/export#examples)

To copy a whole closure, do something like:

```bash
$ nix-store --export $(nix-store --query --requisites paths) > out
```

To import the whole closure again, run:

```bash
$ nix-store --import < out
```
# nix-store --gc
[nix-store --gc documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/gc)
[nix-store --gc documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc#name)

`nix-store --gc` - run garbage collection

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc#synopsis)

```bash
nix-store --gc [ --print-roots | --print-live | --print-dead] [--max-freed _bytes_]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc#description)

Without additional flags, the operation `--gc` performs a garbage collection on the Nix store. That is, all paths in the Nix store not reachable via file system references from a set of “roots”, are deleted.

The following suboperations may be specified:

- `--print-roots`  
    This operation prints on standard output the set of roots used by the garbage collector.
    
- `--print-live`  
    This operation prints on standard output the set of “live” store paths, which are all the store paths reachable from the roots. Live paths should never be deleted, since that would break consistency — it would become possible that applications are installed that reference things that are no longer present in the store.
    
- `--print-dead`  
    This operation prints out on standard output the set of “dead” store paths, which is just the opposite of the set of live paths: any path in the store that is not live (with respect to the roots) is dead.
    

By default, all unreachable paths are deleted. The following options control what gets deleted and in what order:

- `--max-freed` _bytes_  
    Keep deleting paths until at least _bytes_ bytes have been deleted, then stop. The argument _bytes_ can be followed by the multiplicative suffix `K`, `M`, `G` or `T`, denoting KiB, MiB, GiB or TiB units.

The behaviour of the collector is also influenced by the `keep-outputs` and `keep-derivations` settings in the Nix configuration file.

By default, the collector prints the total number of freed bytes when it finishes (or when it is interrupted). With `--print-dead`, it prints the number of bytes that would be freed.

## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-store/gc#examples)

To delete all unreachable paths, just do:

```bash
$ nix-store --gc 
deleting `/nix/store/kq82idx6g0nyzsp2s14gfsc38npai7lf-cairo-1.0.4.tar.gz.drv' 
... 
8825586 bytes freed (8.42 MiB)
```

To delete at least 100 MiBs of unreachable paths:

```bash
$ nix-store --gc --max-freed $((100 * 1024 * 1024))
```
# nix-store --generate-binary-cache-key
[nix-store --generate-binary-cache-key documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/generate-binary-cache-key)
[nix-store --generate-binary-cache-key documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/generate-binary-cache-key)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/generate-binary-cache-key#name)

`nix-store --generate-binary-cache-key` - generate key pair to use for a binary cache

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/generate-binary-cache-key#synopsis)

```bash
nix-store --generate-binary-cache-key _key-name_ _secret-key-file_ _public-key-file_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/generate-binary-cache-key#description)

This command generates an [Ed25519 key pair](http://ed25519.cr.yp.to/) that can be used to create a signed binary cache. It takes three mandatory parameters:

1. A key name, such as `cache.example.org-1`, that is used to look up keys on the client when it verifies signatures. It can be anything, but it’s suggested to use the host name of your cache (e.g. `cache.example.org`) with a suffix denoting the number of the key (to be incremented every time you need to revoke a key).
    
2. The file name where the secret key is to be stored.
    
3. The file name where the public key is to be stored.
# nix-store --import
[nix-store --import documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/import)
[nix-store --import documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/import)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/import#name)

`nix-store --import` - import Nix Archive into the store

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/import#synopsis)

```bash
nix-store --import
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/import#description)

The operation `--import` reads a serialisation of a set of store paths produced by `nix-store --export` from standard input and adds those store paths to the Nix store. Paths that already exist in the Nix store are ignored. If a path refers to another path that doesn’t exist in the Nix store, the import fails.
# nix-store --load-db
[nix-store --load-db documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/load-db)
[nix-store --load-db documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/load-db)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/load-db#name)

`nix-store --load-db` - import Nix database

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/load-db#synopsis)

```bash
nix-store --load-db
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/load-db#description)

The operation `--load-db` reads a dump of the Nix database created by `--dump-db` from standard input and loads it into the Nix database.
# nix-store --optimise
[nix-store --optimise documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/optimise)
[nix-store --optimise documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/optimise)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/optimise#name)

`nix-store --optimise` - reduce disk space usage

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/optimise#synopsis)

```bash
nix-store --optimise
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/optimise#description)

The operation `--optimise` reduces Nix store disk space usage by finding identical files in the store and hard-linking them to each other. It typically reduces the size of the store by something like 25-35%. Only regular files and symlinks are hard-linked in this manner. Files are considered identical when they have the same NAR archive serialisation: that is, regular files must have the same contents and permission (executable or non-executable), and symlinks must have the same contents.

After completion, or when the command is interrupted, a report on the achieved savings is printed on standard error.

Use `-vv` or `-vvv` to get some progress indication.
## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/optimise#example)

```bash
$ nix-store --optimise 
hashing files in `/nix/store/qhqx7l2f1kmwihc9bnxs7rc159hsxnf3-gcc-4.1.1' 
... 
541838819 bytes (516.74 MiB) freed by hard-linking 54143 files; 
there are 114486 files with equal contents out of 215894 files in total
```
# nix-store --print-env
[nix-store --print-env documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/print-env)
[nix-store --print-env documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/print-env)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/print-env#name)

`nix-store --print-env` - print the build environment of a derivation

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/print-env#synopsis)

```bash
nix-store --print-env _drvpath_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/print-env#description)

The operation `--print-env` prints out the environment of a derivation in a format that can be evaluated by a shell. The command line arguments of the builder are placed in the variable `_args`
## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/print-env#example)

```bash
$ nix-store --print-env $(nix-instantiate '<nixpkgs>' -A firefox) 
… 
export src; src='/nix/store/plpj7qrwcz94z2psh6fchsi7s8yihc7k-firefox-12.0.source.tar.bz2' 
export stdenv; stdenv='/nix/store/7c8asx3yfrg5dg1gzhzyq2236zfgibnn-stdenv' 
export system; system='x86_64-linux' 
export _args; _args='-e /nix/store/9krlzvny65gdc8s7kpb6lkx8cd02c25c-default-builder.sh'
```
# nix-store --query
[nix-store --query documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/query)
[nix-store --query documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query#name)

`nix-store --query` - display information about store paths

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query#synopsis)

```bash
nix-store {--query | -q} {--outputs | --requisites | -R | --references | --referrers | --referrers-closure | --deriver | -d | --valid-derivers | --graph | --tree | --binding _name_ | -b _name_ | --has | --size | --roots} [--use-output] [-u] [--force-realise] [-f] _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query#description)

The operation `--query` displays various bits of information about the store paths . The queries are described below. At most one query can be specified. The default query is `--outputs`.

The paths _paths_ may also be symlinks from outside of the Nix store, to the Nix store. In that case, the query is applied to the target of the symlink.

## [Common query options](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query#common-query-options)

- `--use-output`; `-u`  
    For each argument to the query that is a [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation), apply the query to the output path of the derivation instead.
    
- `--force-realise`; `-f`  
    Realise each argument to the query first (see [`nix-store --realise`](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise)).
    

## [Queries](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query#queries)

- `--outputs`  
    Prints out the [output paths](https://nixos.org/manual/nix/unstable/glossary#gloss-output-path) of the store derivations _paths_. These are the paths that will be produced when the derivation is built.
    
- `--requisites`; `-R`  
    Prints out the [closure](https://nixos.org/manual/nix/unstable/glossary#gloss-closure) of the store path _paths_.
    
    This query has one option:
    
    - `--include-outputs` Also include the existing output paths of [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)s, and their closures.
    
    This query can be used to implement various kinds of deployment. A _source deployment_ is obtained by distributing the closure of a store derivation. A _binary deployment_ is obtained by distributing the closure of an output path. A _cache deployment_ (combined source/binary deployment, including binaries of build-time-only dependencies) is obtained by distributing the closure of a store derivation and specifying the option `--include-outputs`.
    
- `--references`  
    Prints the set of [references](https://nixos.org/manual/nix/unstable/glossary#gloss-reference) of the store paths _paths_, that is, their immediate dependencies. (For _all_ dependencies, use `--requisites`.)
    
- `--referrers`  
    Prints the set of _referrers_ of the store paths _paths_, that is, the store paths currently existing in the Nix store that refer to one of _paths_. Note that contrary to the references, the set of referrers is not constant; it can change as store paths are added or removed.
    
- `--referrers-closure`  
    Prints the closure of the set of store paths _paths_ under the referrers relation; that is, all store paths that directly or indirectly refer to one of _paths_. These are all the path currently in the Nix store that are dependent on _paths_.
    
- `--deriver`; `-d`  
    Prints the [deriver](https://nixos.org/manual/nix/unstable/glossary#gloss-deriver) that was used to build the store paths _paths_. If the path has no deriver (e.g., if it is a source file), or if the deriver is not known (e.g., in the case of a binary-only deployment), the string `unknown-deriver` is printed. The returned deriver is not guaranteed to exist in the local store, for example when _paths_ were substituted from a binary cache. Use `--valid-derivers` instead to obtain valid paths only.
    
- `--valid-derivers`  
    Prints a set of derivation files (`.drv`) which are supposed produce said paths when realized. Might print nothing, for example for source paths or paths subsituted from a binary cache.
    
- `--graph`  
    Prints the references graph of the store paths _paths_ in the format of the `dot` tool of AT&T's [Graphviz package](http://www.graphviz.org/). This can be used to visualise dependency graphs. To obtain a build-time dependency graph, apply this to a store derivation. To obtain a runtime dependency graph, apply it to an output path.
    
- `--tree`  
    Prints the references graph of the store paths _paths_ as a nested ASCII tree. References are ordered by descending closure size; this tends to flatten the tree, making it more readable. The query only recurses into a store path when it is first encountered; this prevents a blowup of the tree representation of the graph.
    
- `--graphml`  
    Prints the references graph of the store paths _paths_ in the [GraphML](http://graphml.graphdrawing.org/) file format. This can be used to visualise dependency graphs. To obtain a build-time dependency graph, apply this to a [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation). To obtain a runtime dependency graph, apply it to an output path.
    
- `--binding` _name_; `-b` _name_  
    Prints the value of the attribute _name_ (i.e., environment variable) of the [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)s _paths_. It is an error for a derivation to not have the specified attribute.
    
- `--hash`  
    Prints the SHA-256 hash of the contents of the store paths _paths_ (that is, the hash of the output of `nix-store --dump` on the given paths). Since the hash is stored in the Nix database, this is a fast operation.
    
- `--size`  
    Prints the size in bytes of the contents of the store paths _paths_ — to be precise, the size of the output of `nix-store --dump` on the given paths. Note that the actual disk space required by the store paths may be higher, especially on filesystems with large cluster sizes.
    
- `--roots`  
    Prints the garbage collector roots that point, directly or indirectly, at the store paths _paths_.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-store/query#examples)

Print the closure (runtime dependencies) of the `svn` program in the current user environment:

```bash
$ nix-store --query --requisites $(which svn) 
/nix/store/5mbglq5ldqld8sj57273aljwkfvj22mc-subversion-1.1.4 
/nix/store/9lz9yc6zgmc0vlqmn2ipcpkjlmbi51vv-glibc-2.3.4 ...
```

Print the build-time dependencies of `svn`:

```bash
$ nix-store --query --requisites $(nix-store --query --deriver $(which svn)) 
/nix/store/02iizgn86m42q905rddvg4ja975bk2i4-grep-2.5.1.tar.bz2.drv 
/nix/store/07a2bzxmzwz5hp58nf03pahrv2ygwgs3-gcc-wrapper.sh 
/nix/store/0ma7c9wsbaxahwwl04gbw3fcd806ski4-glibc-2.3.4.drv .
.. lots of other paths ...
```

The difference with the previous example is that we ask the closure of the derivation (`-qd`), not the closure of the output path that contains `svn`.

Show the build-time dependencies as a tree:

```bash
$ nix-store --query --tree $(nix-store --query --deriver $(which svn)) 
/nix/store/7i5082kfb6yjbqdbiwdhhza0am2xvh6c-subversion-1.1.4.drv 
+---/nix/store/d8afh10z72n8l1cr5w42366abiblgn54-builder.sh 
+---/nix/store/fmzxmpjx2lh849ph0l36snfj9zdibw67-bash-3.0.drv 
|   +---/nix/store/570hmhmx3v57605cqg9yfvvyh0nnb8k8-bash 
|   +---/nix/store/p3srsbd8dx44v2pg6nbnszab5mcwx03v-builder.sh ...
```

Show all paths that depend on the same OpenSSL library as `svn`:

```bash
$ nix-store --query --referrers $(nix-store --query --binding openssl $(nix-store --query --deriver $(which svn))) 
/nix/store/23ny9l9wixx21632y2wi4p585qhva1q8-sylpheed-1.0.0 
/nix/store/5mbglq5ldqld8sj57273aljwkfvj22mc-subversion-1.1.4 
/nix/store/dpmvp969yhdqs7lm2r1a3gng7pyq6vy4-subversion-1.1.3 
/nix/store/l51240xqsgg8a7yrbqdx1rfzyv6l26fx-lynx-2.8.5
```

Show all paths that directly or indirectly depend on the Glibc (C library) used by `svn`:

```bash
$ nix-store --query --referrers-closure $(ldd $(which svn) | grep /libc.so | awk '{print $3}') 
/nix/store/034a6h4vpz9kds5r6kzb9lhh81mscw43-libgnomeprintui-2.8.2 
/nix/store/15l3yi0d45prm7a82pcrknxdh6nzmxza-gawk-3.1.4 ...
```

Note that `ldd` is a command that prints out the dynamic libraries used by an ELF executable.

Make a picture of the runtime dependency graph of the current user environment:

```bash
$ nix-store --query --graph ~/.nix-profile | dot -Tps > graph.ps 
$ gv graph.ps
```

Show every garbage collector root that points to a store path that depends on `svn`:

```bash
$ nix-store --query --roots $(which svn) 
/nix/var/nix/profiles/default-81-link 
/nix/var/nix/profiles/default-82-link 
/home/eelco/.local/state/nix/profiles/profile-97-link
```
# nix-store --read-log
[nix-store --read-log documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/read-log)
[nix-store --read-log documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/read-log)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/read-log#name)

`nix-store --read-log` - print build log

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/read-log#synopsis)

```bash
nix-store {--read-log | -l} _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/read-log#description)

The operation `--read-log` prints the build log of the specified store paths on standard output. The build log is whatever the builder of a derivation wrote to standard output and standard error. If a store path is not a derivation, the deriver of the store path is used.

Build logs are kept in `/nix/var/log/nix/drvs`. However, there is no guarantee that a build log is available for any particular store path. For instance, if the path was downloaded as a pre-built binary through a substitute, then the log is unavailable.

## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/read-log#example)

```bash
$ nix-store --read-log $(which ktorrent) 
building /nix/store/dhc73pvzpnzxhdgpimsd9sw39di66ph1-ktorrent-2.2.1 
unpacking sources 
unpacking source archive /nix/store/p8n1jpqs27mgkjw07pb5269717nzf5f8-ktorrent-2.2.1.tar.gz 
ktorrent-2.2.1/ 
ktorrent-2.2.1/NEWS ...
```
# nix-store --realise
[nix-store --realise documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/realise)
[nix-store --realise documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise#name)

`nix-store --realise` - build or fetch store objects

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise#synopsis)

```bash
nix-store {--realise | -r} _paths…_ [--dry-run]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise#description)

Each of _paths_ is processed as follows:

- If the path leads to a [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation):
    
    1. If it is not [valid](https://nixos.org/manual/nix/unstable/glossary#gloss-validity), substitute the store derivation file itself.
    2. Realise its [output paths](https://nixos.org/manual/nix/unstable/glossary#gloss-output-path):
    
    - Try to fetch from [substituters](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-substituters) the [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object) associated with the output paths in the store derivation's [closure](https://nixos.org/manual/nix/unstable/glossary#gloss-closure).
        - With [content-addressed derivations](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-ca-derivations) (experimental): Determine the output paths to realise by querying content-addressed realisation entries in the [Nix database](https://nixos.org/manual/nix/unstable/glossary#gloss-nix-database).
    - For any store paths that cannot be substituted, produce the required store objects:
        1. Realise all outputs of the derivation's dependencies
        2. Run the derivation's [`builder`](https://nixos.org/manual/nix/unstable/language/derivations#attr-builder) executable
- Otherwise, and if the path is not already valid: Try to fetch the associated [store objects](https://nixos.org/manual/nix/unstable/glossary#gloss-store-object) in the path's [closure](https://nixos.org/manual/nix/unstable/glossary#gloss-closure) from [substituters](https://nixos.org/manual/nix/unstable/command-ref/conf-file#conf-substituters).

If no substitutes are available and no store derivation is given, realisation fails.

The resulting paths are printed on standard output. For non-derivation arguments, the argument itself is printed.

## [Special exit codes for build failure](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise#special-exit-codes-for-build-failure)

1xx status codes are used when requested builds failed. The following codes are in use:

- `100` Generic build failure
    
    The builder process returned with a non-zero exit code.
    
- `101` Build timeout
    
    The build was aborted because it did not complete within the specified `timeout`.
    
- `102` Hash mismatch
    
    The build output was rejected because it does not match the [`outputHash` attribute of the derivation](https://nixos.org/manual/nix/unstable/language/advanced-attributes).
    
- `104` Not deterministic
    
    The build succeeded in check mode but the resulting output is not binary reproducible.
    

With the `--keep-going` flag it's possible for multiple failures to occur. In this case the 1xx status codes are or combined using [bitwise OR](https://en.wikipedia.org/wiki/Bitwise_operation#OR).

``0b1100100      ^^^^      |||`- timeout      ||`-- output hash mismatch      |`--- build failure      `---- not deterministic``

## [Options](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise#options)

- `--dry-run`  
    Print on standard error a description of what packages would be built or downloaded, without actually performing the operation.
    
- `--ignore-unknown`  
    If a non-derivation path does not have a substitute, then silently ignore it.
    
- `--check`  
    This option allows you to check whether a derivation is deterministic. It rebuilds the specified derivation and checks whether the result is bitwise-identical with the existing outputs, printing an error if that’s not the case. The outputs of the specified derivation must already exist. When used with `-K`, if an output path is not identical to the corresponding output from the previous build, the new output path is left in `/nix/store/name.check.`

## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-store/realise#examples)

This operation is typically used to build [store derivation](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation)s produced by [`nix-instantiate`](https://nixos.org/manual/nix/unstable/command-ref/nix-instantiate):

```bash
$ nix-store --realise $(nix-instantiate ./test.nix) 
/nix/store/31axcgrlbfsxzmfff1gyj1bf62hvkby2-aterm-2.3.1
```

This is essentially what [`nix-build`](https://nixos.org/manual/nix/unstable/command-ref/nix-build) does.

To test whether a previously-built derivation is deterministic:

```bash
$ nix-build '<nixpkgs>' --attr hello --check -K
```

Use [`nix-store --read-log`](https://nixos.org/manual/nix/unstable/command-ref/nix-store/read-log) to show the stderr and stdout of a build:

```bash
$ nix-store --read-log $(nix-instantiate ./test.nix)
```
# nix-store --repair-path
[nix-store --repair-path documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/repair-path)
[nix-store --repair-path documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/repair-path)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/repair-path#name)

`nix --repair-path` - re-download path from substituter

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/repair-path#synopsis)

```bash
nix-store --repair-path _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/repair-path#description)

The operation `--repair-path` attempts to “repair” the specified paths by redownloading them using the available substituters. If no substitutes are available, then repair is not possible.

> **Warning**
> 
> During repair, there is a very small time window during which the old path (if it exists) is moved out of the way and replaced with the new path. If repair is interrupted in between, then the system may be left in a broken state (e.g., if the path contains a critical system component like the GNU C Library).

## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/repair-path#example)

```bash
$ nix-store --verify-path /nix/store/dj7a81wsm1ijwwpkks3725661h3263p5-glibc-2.13 
path `/nix/store/dj7a81wsm1ijwwpkks3725661h3263p5-glibc-2.13' was modified!   
expected hash `2db57715ae90b7e31ff1f2ecb8c12ec1cc43da920efcbe3b22763f36a1861588',   
got `481c5aa5483ebc97c20457bb8bca24deea56550d3985cda0027f67fe54b808e4' 

$ nix-store --repair-path /nix/store/dj7a81wsm1ijwwpkks3725661h3263p5-glibc-2.13
fetching path `/nix/store/d7a81wsm1ijwwpkks3725661h3263p5-glibc-2.13'...
```
# nix-store --restore
[nix-store --restore documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/restore)
[nix-store --restore documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/restore)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/restore#name)

`nix-store --restore` - extract a Nix archive

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/restore#synopsis)

```bash
nix-store --restore _path_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/restore#description)

The operation `--restore` unpacks a NAR archive to _path_, which must not already exist. The archive is read from standard input.
# nix-store --serve
[nix-store --serve documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/serve)
[nix-store --serve documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/serve)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/serve#name)

`nix-store --serve` - serve local Nix store over SSH

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/serve#synopsis)

```bash
nix-store --serve [--write]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/serve#description)

The operation `--serve` provides access to the Nix store over stdin and stdout, and is intended to be used as a means of providing Nix store access to a restricted ssh user.

The following flags are available:

- `--write`  
    Allow the connected client to request the realization of derivations. In effect, this can be used to make the host act as a remote builder.
## [Examples](https://nixos.org/manual/nix/unstable/command-ref/nix-store/serve#examples)

To turn a host into a build server, the `authorized_keys` file can be used to provide build access to a given SSH public key:

```bash
$ cat <<EOF >>/root/.ssh/authorized_keys 
command="nice -n20 nix-store --serve --write" ssh-rsa AAAAB3NzaC1yc2EAAAA... 
EOF
```
# nix-store --verify-path
[nix-store --verify-path documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/verify-path)
[nix-store --verify-path documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify-path)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify-path#name)

`nix-store --verify-path` - check path contents against Nix database

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify-path#synopsis)

```bash
nix-store --verify-path _paths…_
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify-path#description)

The operation `--verify-path` compares the contents of the given store paths to their cryptographic hashes stored in Nix’s database. For every changed path, it prints a warning message. The exit status is 0 if no path has changed, and 1 otherwise.
## [Example](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify-path#example)

To verify the integrity of the `svn` command and all its dependencies:

```bash
$ nix-store --verify-path $(nix-store --query --requisites $(which svn))
```
# nix-store --verify
[nix-store --verify documentation stable version](https://nixos.org/manual/nix/stable/command-ref/nix-store/verify)
[nix-store --verify documentation unstable version](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify)
## [Name](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify#name)

`nix-store --verify` - check Nix database for consistency

## [Synopsis](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify#synopsis)

```bash
nix-store --verify [--check-contents] [--repair]
```

## [Description](https://nixos.org/manual/nix/unstable/command-ref/nix-store/verify#description)

The operation `--verify` verifies the internal consistency of the Nix database, and the consistency between the Nix database and the Nix store. Any inconsistencies encountered are automatically repaired. Inconsistencies are generally the result of the Nix store or database being modified by non-Nix tools, or of bugs in Nix itself.

This operation has the following options:

- `--check-contents`  
    Checks that the contents of every valid store path has not been altered by computing a SHA-256 hash of the contents and comparing it with the hash stored in the Nix database at build time. Paths that have been modified are printed out. For large stores, `--check-contents` is obviously quite slow.
    
- `--repair`  
    If any valid path is missing from the store, or (if `--check-contents` is given) the contents of a valid path has been modified, then try to repair the path by redownloading it. See `nix-store --repair-path` for details.