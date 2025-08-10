# Flakes 
## Introduction
- new systems to manage distro ecosystems including: nixos configuration, devellopement environment, dérivation, etc
	For comparaison:
	```shell
	python --version
	python: cmd not found
	
	nix-shell -p python
	
	python --version
	Python 2.7.18.5
	```
	or 
	shell.nix
	```shell.nix
	with (import <nixpkgs> {});
	mkShell{
		buildInputs = [
			pkgs.vim
			pkgs.neovim
		];
			
		shellHook = ''
			echo "Hello World"
		'';
	}
	```
	you need to use your channel witch is not good since you have to update
	So there might be not on the same version and will may be break your code
	
	- NixFlakes is easy solution
## Installation
- Add the following to your system configuration (flakes):
	```nix
	  nix.settings.experimental-features = [ "nix-command" "flakes" ];
	```
- Then initiate the flakes (do it in the directory you want to initiate)
	```shell
	nix flake init
	```
## Configuration
- We can modify the flake.nix like this:
	```nix
	{ 
		description = "my epic vims collection"; 
		inputs = { 
			nixpkgs.url = "github:nixos/nixpkgs/nixos-unstable"; 
		}; 
		outputs = { self, nixpkgs }: 
		let 
			system = "x86_64-linux"; 
			pkgs = nixpkgs.legacyPackages.${system}; 
		in { 
			bob = pkgs.mkShell { 
				buildInputs = [ pkgs.neovim pkgs.vim ]; 
				shellHook = '' echo "hello mom" ''; 
			}; 
		}; 
	}
	```
## Launch
```bash
nix develop
```
- To make the shell use BOB
	```bash
	nix develop .#bob
	```
- Update (new version of all dependencie)
	```bash
	nix flakes update
	```
## Extra
### CMD