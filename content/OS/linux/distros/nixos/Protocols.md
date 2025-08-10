# [Protocols](https://nixos.org/manual/nix/unstable/protocols/protocols#protocols)

This chapter documents various developer-facing interfaces provided by Nix.
# [Lockable HTTP Tarball Protocol](https://nixos.org/manual/nix/unstable/protocols/tarball-fetcher#lockable-http-tarball-protocol)

Tarball flakes can be served as regular tarballs via HTTP or the file system (for `file://` URLs). Unless the server implements the Lockable HTTP Tarball protocol, it is the responsibility of the user to make sure that the URL always produces the same tarball contents.

An HTTP server can return an "immutable" HTTP URL appropriate for lock files. This allows users to specify a tarball flake input in `flake.nix` that requests the latest version of a flake (e.g. `https://example.org/hello/latest.tar.gz`), while `flake.lock` will record a URL whose contents will not change (e.g. `https://example.org/hello/<revision>.tar.gz`). To do so, the server must return an [HTTP `Link` header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Link) with the `rel` attribute set to `immutable`, as follows:

```nix
Link: <flakeref>; rel="immutable"
```

(Note the required `<` and `>` characters around _flakeref_.)

_flakeref_ must be a tarball flakeref. It can contain the tarball flake attributes `narHash`, `rev`, `revCount` and `lastModified`. If `narHash` is included, its value must be the NAR hash of the unpacked tarball (as computed via `nix hash path`). Nix checks the contents of the returned tarball against the `narHash` attribute. The `rev` and `revCount` attributes are useful when the tarball flake is a mirror of a fetcher type that has those attributes, such as Git or GitHub. They are not checked by Nix.

```nix
Link: <https://example.org/hello/442793d9ec0584f6a6e82fa253850c8085bb150a.tar.gz   
	?rev=442793d9ec0584f6a6e82fa253850c8085bb150a   
	&revCount=835   
	&narHash=sha256-GUm8Uh/U74zFCwkvt9Mri4DSM%2BmHj3tYhXUkYpiv31M%3D>; rel="immutable"
```

(The linebreaks in this example are for clarity and must not be included in the actual response.)

For tarball flakes, the value of the `lastModified` flake attribute is defined as the timestamp of the newest file inside the tarball.
# [Derivation "ATerm" file format](https://nixos.org/manual/nix/unstable/protocols/derivation-aterm#derivation-aterm-file-format)

For historical reasons, [derivations](https://nixos.org/manual/nix/unstable/glossary#gloss-store-derivation) are stored on-disk in [ATerm](https://homepages.cwi.nl/~daybuild/daily-books/technology/aterm-guide/aterm-guide.html) format.

Derivations are serialised in one of the following formats:

- 1
	```nix
	Derive(...)
	```
    
    For all stable derivations.
    
- 2
	```nix
	DrvWithVersion(<version-string>, ...)
	```
    
    The only `version-string`s that are in use today are for [experimental features](https://nixos.org/manual/nix/unstable/contributing/experimental-features):
    
    - `"xp-dyn-drv"` for the [`dynamic-derivations`](https://nixos.org/manual/nix/unstable/contributing/experimental-features#xp-feature-dynamic-derivations) experimental feature.