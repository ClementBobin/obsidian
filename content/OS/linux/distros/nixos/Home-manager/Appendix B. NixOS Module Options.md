[`home-manager.backupFileExtension`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.backupFileExtension)

On activation move existing files by appending the given file extension rather than exiting with an error.

_Type:_ null or string

_Default:_ `null`

_Example:_ `"backup"`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|

[`home-manager.extraSpecialArgs`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.extraSpecialArgs)

Extra `specialArgs` passed to Home Manager. This option can be used to pass additional arguments to all modules.

_Type:_ attribute set

_Default:_ `{ }`

_Example:_ `{ inherit emacs-overlay; }`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|

[`home-manager.sharedModules`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.sharedModules)

Extra modules added to all users.

_Type:_ list of raw value

_Default:_ `[ ]`

_Example:_ `[ { home.packages = [ nixpkgs-fmt ]; } ]`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|

[`home-manager.useGlobalPkgs`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.useGlobalPkgs)

Whether to enable using the system configuration’s `pkgs` argument in Home Manager. This disables the Home Manager options `nixpkgs.*`.

_Type:_ boolean

_Default:_ `false`

_Example:_ `true`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|

[`home-manager.useUserPackages`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.useUserPackages)

Whether to enable installation of user packages through the `users.users.<name>.packages` option.

_Type:_ boolean

_Default:_ `false`

_Example:_ `true`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|

[`home-manager.users`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.users)

Per-user Home Manager configuration.

_Type:_ attribute set of (Home Manager module)

_Default:_ `{ }`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|

[`home-manager.verbose`](https://nix-community.github.io/home-manager/nixos-options.html#nixos-opt-home-manager.verbose)

Whether to enable verbose output on activation.

_Type:_ boolean

_Default:_ `false`

_Example:_ `true`

_Declared by:_

|   |
|---|
|`[<home-manager/nixos/common.nix>](https://github.com/nix-community/home-manager/blob/master/nixos/common.nix)`|