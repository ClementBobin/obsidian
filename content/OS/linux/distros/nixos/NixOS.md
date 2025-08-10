# NixOS
## Introduction
### Nix
Nix is a _purely functional package manager_. This means that it treats packages like values in purely functional programming languages such as Haskell — they are built by functions that don’t have side-effects, and they never change after they have been built. Nix stores packages in the _Nix store_, usually the directory `/nix/store`, where each package has its own unique subdirectory such as

```
/nix/store/b6gvzjyb2pg0kjfwrjmg1vfhh54ad73z-firefox-33.1/
```

where `b6gvzjyb2pg0…` is a unique identifier for the package that captures all its dependencies (it’s a cryptographic hash of the package’s build dependency graph). This enables many powerful features.

#### [Multiple versions](https://nixos.org/manual/nix/unstable/introduction#multiple-versions)

You can have multiple versions or variants of a package installed at the same time. This is especially important when different applications have dependencies on different versions of the same package — it prevents the “DLL hell”. Because of the hashing scheme, different versions of a package end up in different paths in the Nix store, so they don’t interfere with each other.

An important consequence is that operations like upgrading or uninstalling an application cannot break other applications, since these operations never “destructively” update or delete files that are used by other packages.

#### [Complete dependencies](https://nixos.org/manual/nix/unstable/introduction#complete-dependencies)

Nix helps you make sure that package dependency specifications are complete. In general, when you’re making a package for a package management system like RPM, you have to specify for each package what its dependencies are, but there are no guarantees that this specification is complete. If you forget a dependency, then the package will build and work correctly on _your_ machine if you have the dependency installed, but not on the end user's machine if it's not there.

Since Nix on the other hand doesn’t install packages in “global” locations like `/usr/bin` but in package-specific directories, the risk of incomplete dependencies is greatly reduced. This is because tools such as compilers don’t search in per-packages directories such as `/nix/store/5lbfaxb722zp…-openssl-0.9.8d/include`, so if a package builds correctly on your system, this is because you specified the dependency explicitly. This takes care of the build-time dependencies.

Once a package is built, runtime dependencies are found by scanning binaries for the hash parts of Nix store paths (such as `r8vvq9kq…`). This sounds risky, but it works extremely well.

#### [Multi-user support](https://nixos.org/manual/nix/unstable/introduction#multi-user-support)

Nix has multi-user support. This means that non-privileged users can securely install software. Each user can have a different _profile_, a set of packages in the Nix store that appear in the user’s `PATH`. If a user installs a package that another user has already installed previously, the package won’t be built or downloaded a second time. At the same time, it is not possible for one user to inject a Trojan horse into a package that might be used by another user.

#### [Atomic upgrades and rollbacks](https://nixos.org/manual/nix/unstable/introduction#atomic-upgrades-and-rollbacks)

Since package management operations never overwrite packages in the Nix store but just add new versions in different paths, they are _atomic_. So during a package upgrade, there is no time window in which the package has some files from the old version and some files from the new version — which would be bad because a program might well crash if it’s started during that period.

And since packages aren’t overwritten, the old versions are still there after an upgrade. This means that you can _roll back_ to the old version:

```bash
$ nix-env --upgrade --attr nixpkgs.some-package 
$ nix-env --rollback
```

#### [Garbage collection](https://nixos.org/manual/nix/unstable/introduction#garbage-collection)

When you uninstall a package like this…

```bash
$ nix-env --uninstall firefox
```

the package isn’t deleted from the system right away (after all, you might want to do a rollback, or it might be in the profiles of other users). Instead, unused packages can be deleted safely by running the _garbage collector_:

```bash
$ nix-collect-garbage
```

This deletes all packages that aren’t in use by any user profile or by a currently running program.

#### [Functional package language](https://nixos.org/manual/nix/unstable/introduction#functional-package-language)

Packages are built from _Nix expressions_, which is a simple functional language. A Nix expression describes everything that goes into a package build task (a “derivation”): other packages, sources, the build script, environment variables for the build script, etc. Nix tries very hard to ensure that Nix expressions are _deterministic_: building a Nix expression twice should yield the same result.

Because it’s a functional language, it’s easy to support building variants of a package: turn the Nix expression into a function and call it any number of times with the appropriate arguments. Due to the hashing scheme, variants don’t conflict with each other in the Nix store.

#### [Transparent source/binary deployment](https://nixos.org/manual/nix/unstable/introduction#transparent-sourcebinary-deployment)

Nix expressions generally describe how to build a package from source, so an installation action like

```bash
$ nix-env --install --attr nixpkgs.firefox
```

_could_ cause quite a bit of build activity, as not only Firefox but also all its dependencies (all the way up to the C library and the compiler) would have to be built, at least if they are not already in the Nix store. This is a _source deployment model_. For most users, building from source is not very pleasant as it takes far too long. However, Nix can automatically skip building from source and instead use a _binary cache_, a web server that provides pre-built binaries. For instance, when asked to build `/nix/store/b6gvzjyb2pg0…-firefox-33.1` from source, Nix would first check if the file `https://cache.nixos.org/b6gvzjyb2pg0….narinfo` exists, and if so, fetch the pre-built binary referenced from there; otherwise, it would fall back to building from source.

#### [Nix Packages collection](https://nixos.org/manual/nix/unstable/introduction#nix-packages-collection)

We provide a large set of Nix expressions containing hundreds of existing Unix packages, the _Nix Packages collection_ (Nixpkgs).

#### [Managing build environments](https://nixos.org/manual/nix/unstable/introduction#managing-build-environments)

Nix is extremely useful for developers as it makes it easy to automatically set up the build environment for a package. Given a Nix expression that describes the dependencies of your package, the command `nix-shell` will build or download those dependencies if they’re not already in your Nix store, and then start a Bash shell in which all necessary environment variables (such as compiler search paths) are set.

For example, the following command gets all dependencies of the Pan newsreader, as described by [its Nix expression](https://github.com/NixOS/nixpkgs/blob/master/pkgs/applications/networking/newsreaders/pan/default.nix):

```bash
$ nix-shell '<nixpkgs>' --attr pan
```

You’re then dropped into a shell where you can edit, build and test the package:

```bash
[nix-shell]$ unpackPhase 
[nix-shell]$ cd pan-* 
[nix-shell]$ configurePhase 
[nix-shell]$ buildPhase 
[nix-shell]$ ./pan/gui/pan
```

#### [Portability](https://nixos.org/manual/nix/unstable/introduction#portability)

Nix runs on Linux and macOS.

### NixOS
NixOS is a modern, open-source operating system built on the Nix package manager. It is designed to provide a declarative and purely functional approach to system configuration and package management. NixOS stands out from other Linux distributions due to its unique features and philosophies.

#### Key Features

#### 1. **Declarative System Configuration**

NixOS employs a declarative configuration model. System configuration is described in a configuration file, typically `/etc/nixos/configuration.nix`. This approach allows users to define the desired state of the system explicitly, making it easy to understand and reproduce configurations.

#### 2. **Immutable Packages and Rollbacks**

Nix, the package manager used by NixOS, manages packages in an immutable fashion. This immutability ensures that packages do not change after installation, promoting consistency and stability. Additionally, NixOS supports easy rollbacks, enabling users to revert to a previous system configuration if needed.

#### 3. **Atomic Upgrades**

NixOS supports atomic upgrades, meaning system updates are performed as a single, atomic transaction. This ensures that either all updates are applied successfully, or none of them are, preventing potential system inconsistencies.

#### 4. **Functional Package Management**

Packages in NixOS are built using a functional approach. Each package is isolated and built in its own environment, with all dependencies specified explicitly. This eliminates dependency conflicts and allows for reproducible builds.

#### 5. **Nix Expression Language**

The Nix package manager and NixOS use a unique functional programming language for configuration called the Nix Expression Language (Nix). Nix provides a powerful and flexible way to describe packages and system configurations.

#### Use Cases

- **Development Environments**: NixOS is well-suited for creating consistent and isolated development environments, making it easier for developers to manage dependencies.
    
- **Server Environments**: Its declarative configuration and atomic upgrades make NixOS a strong choice for server setups where reliability and maintainability are crucial.
    
- **Reproducible Systems**: NixOS is ideal for creating reproducible systems, ensuring that a system's state can be replicated across different machines.
    
#### Point of use
1. Linux distribution based on Nix Package manager
2. Supports declarative reproducible system configuration
3. "Unbreakable"
	- Boot to specific configuration generations. (as mentioned above -> reproducible)
4. nix-store: no /lib & /usr/lib. almost non-existant /bin & /usr/bin -> /nix/store
5. nix-env: install packages at user level without having to change system state

#### Conclusion

NixOS provides a unique and powerful approach to operating system configuration and package management. Its declarative model, immutable packages, and functional design make it a compelling choice for those seeking reliability, consistency, and ease of management in their computing environments. Whether for development or production use, NixOS offers a fresh perspective on how we interact with and manage operating systems.

## Getting Started
- NixOS Website
	- [NixOS](https://nixos.org/)
	- [Manual](https://nixos.org/manual/nixos/stable/) Downloads -> NixOS -> More -> Manual
	- [Unstable](https://releases.nixos.org/?prefix=nixos/unstable/) Downloads -> NixOS -> More -> also available
- Burn ISO
- Partitioning
	- GUI: gparted
		- install gparted
			```shell 
			systemctl start display-manager
			```
		- Device -> Create partition table -> msdos (legacy boot) (old computer / one partition / not dual boot)
										->gpt (uefi boot) (pc>2TO)
		- Add new partition -> fileSystem: ext4/linux-swap
		- Manage flags -> boot for ext4 (possible not necessary)
		- label partitions (useful later)
	- Terminal: Parted
		These step are for a fresh installation. Not dual boot
		```shell
		parted /dev/sda -- mklabel msdos (gpt for uefi)
		```
		```shell
		parted /dev/sda -- mkpart primary 1MIB 100% (512MIB -8GIB for uefi)
		```
		```shell
		parted /dev/sda -- mkpart primary linux-swap -8GIB 100%
		```
		Extra for UEFI
		```shell
		parted /dev/sda -- mkpart ESP fat32 1Mib 512MIB
		```
		```shell
		parted /dev/sda -- set 3 esp on
		```

		```shell
		mkfs.ext4 -L nixos /dev/sda1
		```
		```shell
		mkswap -L swap /dev/sda2
		```
		Extra for UEFI
		```shell
		mkfs.fat -F 32 -n boot /dev/sda3
		```
	- Mounting
		```shell
		mount /dev/disk/by-label/nixos /mnt
		```
		Extra for UEFI
		```shell
		mkdir -p /mnt/boot
		```
		```shell
		mount /dev/disk/by-label/boot /mnt/boot
		```

		```shell
		swapon /dev/sda2
		```
		If you don't know the name of your disk:
		```shell
		lsblk -f
		```
### Encrypt Disk
1. **Warning: be extremely careful with disk labels when following this tutorial.** Devices and partitions may appear under different labels on your system. Using commands like `dd` or `cryptsetup luksFormat` will cause permanent data loss! Use `lsblk` in order to check disk labels if at all unsure.

All commands must be run as the `root` user. This may be done using `sudo`, or by opening a root shell. In order to open a root shell, simply run:

```bash
sudo su root
```

#### Prepare Disks

This step is entirely optional. We will prepare the disk devices by erasing them. We will first _zeroise_ `/dev/sdb`, in order to completely wipe it.

```bash
dd if=/dev/zero of=/dev/sdb status=progress
```

Next, we will wipe `/dev/sda` by filling it with random data.

```bash
dd if=/dev/urandom of=/dev/sda status=progress
```

The reason we wipe the primary device by filling it with random data, instead of simply zero-ising it, is to make the size of the encrypted content undeterminable.

Now `/dev/sda` and `/dev/sdb` are fully prepared. We are ready to create partition tables, and partitions within them.

#### Create Partitions

We will have the following partition scheme. The specific [method (or scenario)](https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#Overview) that we will implement for our Full Disk Encryption (FDE) is to mount an [LVM (Logical Volume Manager)](https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29) on top of our LUKS2 Container. LVM volumes are then created to reflect the different partitions on our root filesystem. This method is referred to as [LVM on LUKS](https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS) and is a common method of implementing FDE on Linux devices.

`/dev/sda` **Primary device**

- `/dev/sda1` LUKS2 Container `crypted`
- LVM Volume Group `vg`
- LVM Logical Volume `vg-swap`
- LVM Logical Volume `vg-nixos`
- and any other partitions...

`/dev/sdb` **Portable device**

- `/dev/sdb1` `boot` Partition
- `/dev/sdb2` LUKS2 Detached Header

The underlying root `\`, `\home`, and swap partitions will be created as LVM virtual volumes within the LUKS2 container.

We will first proceed to make the partition table and partition for the primary `/dev/sda` device, then for the portable `/dev/sdb` device. We will be using `parted` as the tool to create partitions.

##### Make root partition on primary device `/dev/sda`

We will be using the [`parted` command-line tool](https://www.gnu.org/software/parted/manual/parted.html) to create all of our partitions.

Create a [`gpt` partition table](https://en.wikipedia.org/wiki/GUID_Partition_Table) for `/dev/sda`. Other partition table formats like `msdos` are not necessary.

```bash
parted /dev/sda -- mklabel gpt
```

Create primary partition for `/dev/sda`. This will take up all of the space on the primary `/dev/sda` device, since it will hold a LUKS2 encryption container. Other partitions (such as swap, or `/home`) will be created within the encryption container.

```bash
parted /dev/sda -- mkpart primary 0% 100%
```

The partition setup for the primary `/dev/sda` device is now complete. We will now proceed to partition the `/dev/sdb` portable device (i.e. the USB, MicroSD card).

##### Make boot partition on portable device `/dev/sdb`

Create a `gpt` partition table for `/dev/sdb`.

```bash
parted /dev/sdb -- mklabel gpt
```

Create boot partition for `/dev/sdb`. This is the unencrypted partition that will contain the bootloader for the operating system. It will reside on the portable device, which should be stored securely when not in use.

```bash
parted /dev/sdb -- mkpart ESP fat32 0% 50%
```

We must set some flags to indicate that this partition contains the bootloader.

```bash
parted /dev/sdb -- set 1 boot on
```

Now we will use the remaining space on the portable device to create a partition for the LUKS2 detached header. This partition will not actually contain a filesystem, since the LUKS2 detached header will be read as a raw header.

```bash
parted /dev/sdb -- mkpart primary 50% 100%
```

I choose to devote the remaining 50% of the device's space, simply because the MicroSD card will not be used for any other purpose. However, in practice a smaller partition can be allocated for the LUKS2 detached header. Unlike LUKS1, the detached header [does not have a static, fixed size](https://security.stackexchange.com/a/227358). However in practice a partition of 16MB should be more than enough.

#### Make filesystem for boot partition

We will make a `FAT32` filesystem for the boot partition. We are using `FAT32` instead of `ext4` for greater compatibility with bootloaders.

```bash
mkfs.fat -F 32 -n boot /dev/sdb1
```

It is not necessary to make a filesystem for the LUKS2 header partition `/dev/sdb2`. This is because the LUKS2 header will reside as a _raw_ header without any underlying file system. This avoids the complications of the bootloader having to mount a filesystem before reading the header file.

#### Make LUKS2 Encryption Container with detached headers

We will now use the `cryptsetup` command to create the LUKS2 Encryption container. We will invoke the `luksFormat` action on `/dev/sda1` in order to do so. The command comes with a set of sensible and sane cryptographic defaults, however you may choose to explore [further configuration options](https://wiki.archlinux.org/title/Dm-crypt/Device_encryption#Encryption_options_for_LUKS_mode) if you desire.

The location of the LUKS2 wrapper is on the primary hard drive `/dev/sda1`.

The LUKS2 header which contains the metadata is on raw partition `/dev/sdb2`

This command will prompt you to enter a password. This password will be used to unlock the primary device when the computer boots.

```bash
cryptsetup luksFormat /dev/sda1 --type luks2 --header /dev/sdb2
```

#### Open LUKS2 Container

A LUKS2 container has been created on `/dev/sda1`, with it's corresponding header file located at `/dev/sdb2`.

In order to use this container, we must unlock it using the following command. You will be asked to input the decryption password from the previous step.

```bash
cryptsetup luksOpen /dev/sda1 crypted --header /dev/sdb2
```

Now the container will be available as `crypted`, at `/dev/mapper/crypted`.

#### Create a LVM Volume within the LUKS2 Container

We will now create a set of LVM volumes within the LUKS2 container. This way we may have other multiple logical partitions within the container itself.

First, we will initialise the physical volume `crypted`. This step is necessary in order to create logical volumes within it.

```bash
pvcreate /dev/mapper/crypted
```

Next, we will create a volume group upon the newly-initialised physical volume. This volume group will be called `vg`.

```bash
vgcreate vg /dev/mapper/crypted
```

Now that the volume group is made, we can make arbitrary logical volumes. These logical volumes correspond to the unencrypted partitions of a traditional Linux installation.

Although it is possible to make multiple partitions corresponding to different mount points (such as `/home`, `/etc`, `var`, etc), in practice this is not necessary. This is because the main benefit of having a separate `/home` partition is easier recovery, where the `/home` partition can be mounted separately in a rescue process.

Because all partitions reside within the encrypted LUKS2 container, which must be unlocked for access, there is no benefit to having separate partitions. Hence we will only create a root and swap partition.

##### Create a swap partition within the LVM volume

Create a [swap partition](https://en.wikipedia.org/wiki/Memory_paging#Unix_and_Unix-like_systems) with the label `swap`. Note that we use the option `-L` which denotes a numerical size. In the following command, a 16 GB swap partition is created.

```bash
lvcreate -L 16G -n swap vg
```

There are [differing opinions](https://askubuntu.com/questions/62073/how-to-decide-on-swap-size) on the appropriate size for a swap partition on modern Linux. In particular, if you wish to to enable [hibernation](https://www.kernel.org/doc/html/latest/power/basic-pm-debugging.html) you must have the same amount of swap as your RAM.

##### Create a root partition within the LVM volume

Create a root partition with the label `nixos` using the remaining free space. Note that we use the option `-l` which denotes a percentage.

```bash
lvcreate -l '100%FREE' -n nixos vg
```

Now the LVM volumes are created, and ready to be used.

#### Create Filesystem and Swap

After creating the volumes, we must create filesystems that will reside on them. For this guide, we will use a relatively ordinary [`ext4` filesystem](https://en.wikipedia.org/wiki/Ext4). You may substitute more exotic filesystems such as [`ZFS`](https://en.wikipedia.org/wiki/ZFS) or [`btfs`](https://en.wikipedia.org/wiki/Btrfs) if desired.

```bash
mkfs.ext4 -L nixos /dev/vg/nixos
mkswap -L swap /dev/vg/swap
```

After creating the filesystems, we will mount them (and activate swap).

#### Mount filesystems

Mount the root partition

```bash
mount /dev/disk/by-label/nixos /mnt
```

Mount the boot partition

```bash
mkdir -p /mnt/boot
mount /dev/sdb1 /mnt/boot
```

Activate swap

```bash
swapon /dev/vg/swap
```

Now our filesystems are mounted. The future NixOS installation's root will be accessible at `/mnt`, and it's boot partition at `/mnt/boot`.

#### Configure NixOS

We can now instruct NixOS to generate a set of configuration files for our installation. Make sure to pass the `--root /mnt` flag, in order to indicate where the root filesystem resides.

```bash
nixos-generate-config --root /mnt
```

Now the configuration files will be available at `/mnt/etc/nixos`. We must modify this file in order to add the appropriate settings.

##### Configure configurations.nix

We can now specify the configuration of the NixOS installation using `configurations.nix`. The included example configuration file has various options that can be explored. In particular, you should check out the following:

- [User configuration](https://nixos.org/manual/nixos/stable/index.html#sec-user-management)
- [Enabling NetworkManager for WiFi](https://nixos.org/manual/nixos/stable/index.html#sec-networkmanager)

Once generic configurations are complete, we must add the specific `boot.initrd.luks.devices` settings which will allow the system to boot.

The following section must be added. We are specifying for NixOS that there is a dictionary of `boot.initrd.luks.devices`, where there exists a device `crypted` with configuration options enclosed in another dictionary.

```nix
# Configuration options for LUKS Device
boot.initrd.luks.devices = {
  crypted = {
    device = "/dev/disk/by-partuuid/<PARTUUID of /dev/sda1>";
    header = "/dev/disk/by-partuuid/<PARTUUID of /dev/sdb2>";
    allowDiscards = true; # Used if primary device is a SSD
    preLVM = true;
  };
};
```

We must specify the `device` directive which is a path that points to the encrypted primary partition `/dev/sda1`, as well as `header` which is a path that points to the LUKS2 Header located on `/dev/sdb2`.

These paths can be specified in more than one way. You can see the various ways that this path is specified by listing the subdirectories in `/dev/disk`.

I recommend specifying the paths using `/dev/disk/by-partuuid` instead of `/dev/disk/by-uuid`, because `/dev/sda1` does not have a `uuid` assigned to it, since it doesn't have a filesystem.

Hence in order to find the UUIDs of /dev/sda1 and /deb/sdb2, run:

`blkid /dev/sda1 -s PARTUUID`

Or you may simply run `ls -l /dev/disk/by-partuuid`

##### Installation

After setting the configuration options, it is time to install the device. You will need to have an internet connection, as NixOS will be downloading and compiling sources. Either connect to an ethernet cable, or a WiFi network.

Now run `nixos-install`. We will specify the option `--cores 0` to let NixOS use all CPU cores when compiling binaries.

```bash
nixos-install --root /mnt --cores 0
```

This command will take anywhere from 5 to 25 minutes, depending on the configuration of the system and the speed of the internet connection.

Once the installation is nearly complete, it will prompt you to set a root password for the newly installed system. After setting the password, the installation is complete.

```bash
reboot
```

#### Post-Installation

When the installation is complete, perform a reboot. Now you must enter the BIOS/UEFI interface of your computer's firmware, and change it's boot settings to use the bootloader located on the portable device `/dev/sdb1` by default.

Now your NixOS installation is complete
## Initial configuration
- Generate
	- Generate default configuration:
		```shell
		nixos-generate-config --root /mnt
		```
	- Location:
		```shell
		cd /mnt/etc/nixos/
		```
- Configuration.nix
	- General
		- Argument on how to evaluate config:
			\[config, pkgs, ...]:
		- Pull in other files used within the config:
			import = \[./hardware-configuration.nix]:
	- Boot
		- Legacy
			- Only viable if dualbooting linux distributions
			```shell
			# Default Grub setup
			boot.loader.grub.enable = true;
			boot.loader.grub.version = 2;
			boot.loader.grub.device = "/dev/vda": # if virtual machine
			# Dual booting made easy (Optional)
			boot.loader.grub.userOSProber = true;
			# Dual booting made a bit harder (Extra Optional)
			boot.loader.grub.extraEntries = ''
				menuentry "Windows 10" {
					chainloader (hd0,1)+1
				}
			'';
			```
			OR
			```shell
			boot.loader.grub = {
				enable = true;
				version = 2;
			};
			```
		- UEFI
			- Used for larger boot drives and dual booting with windows
				```bash
				# Default UEFI setup
				boot.loader.systemd-boot.enable = true;
				boot.loader.efi.canTouchEfiVariables = true;
				# Dual booting using grub
				boot.loader = {
					efi = {
						canTouchEfiVariables = true;
						efiSysMountPoint = "/boot/efi"; # /boot will probably work too 
					};
					grub = { # Using grub means first 2 lines can be removed
						enable = true;
						#device = ["nodev"];     # Generate boot menu but not actually installed
						devices = ["nodev"];     # Install grub
						efiSupport = true;
						useOSProber = true;      # Or use extraEntries like seen with legacy
					};  # OSProber will probably not find windows partition on first install
				};
				```
		- Extras
			```bash
			{ pkgs, ... }:
			
			{
				boot = {
					kernelPackages = pkgs.linuxPackages_latest; # Get latest kernel
					initrd.kernelModules = ["amdgpu"]; # More on this later on (setting it for xserver)
					loader = {
						#efi = {
							#canTouchEfiVariables = true;
							#efiSysMountPoint = "/boot/efi";
						#};
						grub = {
							#enable = true;
							#devices = ["nodev"];
							#efiSupport = true;
							#useOSProber = true;
							configurationLimit = 5; #Limit stored system "backup configuration".
						}; #Also exists for systemd-boot
						timeout = 5; #Work for grub and efi boot, time before auto-boot
					};
				};
			}
			```
	- Networking
		- Uncomment: networking.hostName="nixos";
			- networking.hostName="nixos";
			- networking.wireless.enable = true; or networking.networkmanager.enable = true;               // for laptop or wireless chose one 
		- Network card details 
		
		//could.be.moved.to.hardware-configuration.nix
		- Deprecated but keep: networking.useDHCP = false;
		- Just internet via ethernet: networking.interfaces.<networkcard-id%>.useDHCP = true;
		
		- Extra
			- Can be transfer in Configuration.nix
			```bash
			networking = {
				#hostName = "nixos";
				#networkmanager.enable = true;
				#wireless.enable = true;
				interfaces = {
					<networkcard-id%> = {
						#useDHCP = true;
						#ipv4.addresses = [ { # Ofcourse not compatible with networkmanager 
							#address = "192.168.0.50";
							#prefixLength = 24;
						#}];
					};
				};
				defaultGateway = "192.168.0.1";
				nameservers = [ "1.1.1.1" ];
			};
			```
	- Internationalisation
		*Where am i? How do i work*
		```bash
		# Clock
		time.timeZone = "Europe/Paris";
		# Locale
		i18n.defaultLocale = "en_US.UTF-8";
		i18n.extraLocaleSettings = {
			LC_TIME = "nl_FR.UTF-8";
			LC_MONETARY = "nl_FR.UTF-8";
		};
		# TTY layout
		console = {
			font = "...";
			keymap = "azerty"; # us / fr /azerty /etc... 
		};
		# XServer layout (possibly also sets console now)
		services.xserver.layout = "azerty" # us / fr /azerty /etc...
		# Extra keyboard settings:
		services.xserver.xkbOptions = "eurosign:e"; # For exemple adds €
		```
	- Display Managers/desktop Environments/Window Managers
		- *Default*
			```bash
			services.xserver.enable = true;
			services.xserver.displayManager.sddm.enable = true;
			services.xserver.desktopManager.plasma5.enable = true;
			```
		- *Customized*
			```bash
			services = {
				xserver = { 
					enable = true;
					displayManager = {
						lightdm.enable = true; # Whether to enable lightdm as the display manager.
						defaultSession = "none+bspwm"; # Graphical session to pre-select in the session chooser "desktopManager + windowManager" or if don't want a backend desktop manager "none + windowManager"
					};
					desktopManager.xcfe.enable = true; # xcfe desktop environement
					windowManager.bspwm.enable = true; # enable bspwm.
				};
			};
			```
	- Hardware
		- Audio & Bluetooth
			- PulseAudio Wiki
			- Bluetooth Wifi (+ configuring it with PulseAudio)
			
			- Example
				```bash
				{ pkgs, ... }:
				
				{
					sound = {
						enable = true;
						mediaKeys.enable = true;
					};
					hardware.bluetooth = {
						enable = true;
						hsphfpd.enable = true; # HSP  HFS daemon
						settings = {
							General = {
								Enable = "Source,Sink,Media,Socket";
							};
						};
					};
				}
				```
		- Touchpad
			- Libinput Options
			```bash
			services.xserver.libinput = {
				enable = true;
				#tapping = true;
				#naturalScrolling = true;
				# ...
			}
			```
	- Users
		```bash
		users.users.<name> = {
			isNormalUser = true;
			extraGroups = [ "wheel" "video" "audio" "networkmanager" "lp" "scanner" ]
			#initialPassword = "password"; #not recomanded
			#shell = pkgs.zsh;
		}
		```
	- Packages
		```bash
		environment.systemPackages = with pkgs; [
			vim
			wget
			git
			#pkgs.firefox
			firefox
		];
		```
	- StateVersion
		- No need to touch this.
		- Nothing to do with the version of the system.
		- Just tells the version of state/config
		- Can be updates to a stable version if you are really sure.
- Hardware-configuration.nix
	- Generate
		- Also get automatically generated with:
			`# nixos-generate-config --root /mnt`
		- Should detect mounted drives, device parts, kernelModules, etc... that are needed
		- Can be deleted and regenerated with:
			`# nixos-generate-config`
		- Reproduction
			- This represent the root
			```bash
			fileSystems."/" =
			{ device = "/dev/disk/by-label/name"; # change name by the name of your drive
			  fsType = "ext4";
			};
			```
	- File System
		- 
## Installation
- System
	- For initial installation:
		```bash
		nixos-install
		```
	- After applying changes to the config:
		```bash
		nixos-rebuild switch
		```
	- Lastly: set a root password
- Login
	- initialPasword
		- Log in with give password of  `users.users.<users>.initialPassword`
		- then change password
			```bash
			sudo passwd <user>
			```
	- via TTY
		- Ctrl + Alt + F1 -> log in via root
		```bash
		passwd <user>
		```
		- Ctrl + Alt + F7 -> log in via user
## Declaring packages, services, settings, etc
- Options
	- Individually via Nix Package Manager ( not permanent )
		Install: 
		```bash
		nix-env -iA nixos.firefox
		```
		List:
		```bash
		nix-env -q
		```
		Uninstall:
		```bash
		nix-env --uninstall firefox
		```
	- Configuration file: 
		- [[OS/linux/distros/nixos/NixOS#Initial configuration]]
- Links
	- [Packages](https://search.nixos.org/packages?channel=unstable&size=50&sort=relevance&type=packages)
	- [Options](https://search.nixos.org/options?channel=unstable&size=50&sort=relevance&type=packages)
	```bash
	man configuration.nix
	```
- Declaring Packages
	*Installed Systemwide*
	```bash
	environment = {
		systemPackages = with pkgs; [
			plex
			superTux
		];
	};
	
	nixpkgs.config.allowUnfree = true;
	```
- Declaring Option
	*Some packages will also have options to configure it further*
	```bash
	services = {
		plex = {
			enable = true;
			openFirewall = true;
		};
	};
	```
- Variables
	*Values that can change often or you want to use multiple times*
	```nix
	let
		rofi-theme = {
			"*" = {
				bg = "#FFFFFF";
			};
		};
	in
	{
		programs.rofi = {
			enable = true;
			theme = rofi-theme;
		};
	};
	```
- Overlays
	*Change packages or add new packages to existing in nix*
	- [Overlays wiki](https://nixos.wiki/wiki/Overlays)
	```bash
	nixpkgs.overlays = [
		(self: super: {
			sl = super.sl.overrideAttrs (old: {
				src = super.fetchFromGitHub {
					owner = 'mtoyoda';
					repo = "sl";
					rev = "923e7d7ebc5c1f009755bdeb789ac25658ccce03";
					sha256 = "0000000000000000000000000000000000000000000000000000"; # if use flakes
				};
			});
		})
	
		(self: super: {
			discord = super.discord.overrideAttrs (
				_: { src = builtins.fetchTarball {
					url = "https: //discord.com/api/download?platform=linux&format=tar.gz";
					sha256 = "0000000000000000000000000000000000000000000000000000"; # if use flakes
				}; }
			);
		})
	];
	# Should be the same for home-manager
	```
- Applying
	```bash
	sudo nixos-rebuild switch
	```
## Extras
- Updating & Upgrading
	- Nix-channel
		A. 
		```bash
		nix-channel --add https://nixos.org/channels/nixos-21.11
		```
		OR
		B.
		```bash
		nix-channel --update
		```
		2. Next rebuild, use the --upgrade flag:
		```bash
		sudo nixos-rebuild --upgrade
		```
		
		D. Installed through nix-env:
		```bash
		nix-env -u '*'
		```
	- Configuration.nix
		```nix
		system.autoUpgrade = {
			enable = true;
			channel = "https://nixos.org/channels/nixos-unstable";
			dates = "weekly";
		};
		```
- Garbage Collection
	- Command line
		- Remove undeclared packaged, dependencies and symlinks:
			```bash
			nix-collect-garbage
			```
		- Remove above of older generations:
			```bash
			nix-collect-garbage --delete-olg
			```
			List Generations
			```bash
			nix-env --list-generations
			```
		- Remove specific generations or older than ... days:
			```bash
			nix-env --delete-generations 14d
			```
			```bash
			nix-env --delete-generations 10 11
			```
			Optimize store:
			```bash
			nix-store --gc
			```
		- All in one:
			```bash
			nix-collect-garbage -d
			```
	- Configuration.nix
		```nix
		nix = {
			settings.auto-optimise-store = true;
			gc = {
				automatic = true;
				dates = "monthly";
				options = "--delete-older-than 7d";
			};
		};
		```
# NixOS Server 
## Introduction 
NixOS is a modern, open-source operating system that provides a declarative and purely functional approach to system configuration and package management. This guide will walk you through setting up a NixOS server. 
## Getting Started 
Before you begin with the installation and configuration, make sure you have the necessary hardware and a basic understanding of Linux concepts and server management. 
![[OS/linux/distros/nixos/NixOS#NixOS#Initial configuration]]]
## Initial Configuration 
Ensure that you have a clear understanding of the system requirements and the specific configuration you want to achieve for your NixOS server. Decide on the necessary hardware specifications, network settings, and other relevant parameters. 
## Installation 
### Server
Use [minimal iso image](https://channels.nixos.org/nixos-23.05/latest-nixos-minimal-x86_64-linux.iso) to create a server
then follow config
### Virtualbox
#### Using OVA 
- Download the OVA file [here](https://channels.nixos.org/nixos-23.05/latest-nixos-x86_64-linux.ova).
- Open VirtualBox.
- Run `File → Import Appliance` from the menu.
- Select previously downloaded OVA file.
- Click `Import`.
- You can then start the virtual machine.
- You can log in as **user `demo`**, **password `demo`**.
- To obtain a root shell, run `sudo -i` in the terminal (`konsole`).
#### Normal install
[[OS/linux/distros/nixos/NixOS#Installation]]
### AWS Command Line

You can also create an instance from the command line. For example, to create an instance in region `eu-west-1` using the EC2 API tools, just run:

```bash
$ nix-shell -p ec2_api_tools
(nix-shell) 
$ ec2-run-instances ami-0fc7825fe890f87d1 --region eu-west-1 -k _my-key-pair_
```
### Docker
- here is the docker machine [link](https://hub.docker.com/r/nixos/nix)
```
FROM nixos/nix

RUN nix-channel --update

RUN nix-build -A pythonFull '<nixpkgs>'
```
#### Docker Pull Command

```
docker pull nixos/nix
```
#### Limitations

By default [sandboxing](https://nixos.org/manual/nix/stable/#conf-sandbox) is turned off inside the container, even though it is enabled in new installations of nix. This can lead to differences between derivations built inside a docker container versus those built without any containerization, especially if a derivation relies on sandboxing to block sideloading of dependencies.

To enable sandboxing the container has to be started with the [`--privileged`](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities) flag and `sandbox = true` set in `/etc/nix/nix.conf`.
## Config

## Extras 
Explore additional features and optimizations for your NixOS server: 
- Setting Up Services 
	Configure and manage services on your NixOS server, such as web servers, databases, and more. 
- Customizing Packages 
	Learn how to customize packages and manage dependencies using the Nix package manager. 
- Security Measures 
	Implement security best practices to protect your NixOS server from potential threats. 
-  Monitoring and Logging Set up monitoring tools and log management to keep track of server performance and activities. 
# Home-Manager
## Introduction
- It's like configuration.nix, but for the user environment.
- Plenty more option to declare packages
- Also a better way to manage dotfiles
- "sudo" nix but home-manager "its not a sudo so only for the user and more option"
## Getting Started
- Home-Manager Website
	- [Github](https://github.com/nix-community/home-manager/)
	- [Manual](https://nix-community.github.io/home-manager/)
	- [Appendix A](https://nix-community.github.io/home-manager/options.html)
	- [Appendix B](https://nix-community.github.io/home-manager/nixos-options.html)
- Setup
	- Initial
		*As a user*
		- Add the channel: *need  to be run with root privileges if you want to use the NixOS Module*
			Unstable version
			```bash
			nix-channel --add https://github.com/nix-community/home-manager/archive/master.tar.gz home-manager
			```
			or LTS
			```bash
			nix-channel --add https://github.com/nix-community/home-manager/archive/release-21.11.tar.gz home-manager
			```
		- `nix-channel --update`
		- just to be sure, relog
	- NixOS Module
		*Add to configuration.nix*
		```nix
		let
		in
		{
			import = [ <home-manager/nixos> ];
			
			users.users.<name> = {
				isNormalUser = true;
			}
			
			home-manager.users.<name> = { pkgs, ... }: {
				# declared packages. for example:
				home.packages = with pkgs; [ 
					atool 
					httpie 
				];
			};
		}
		```
	- Standalone
		- Installation
			```bash
			nix-shell '<home-manager>' -A install
			```
		- Configuration file:
			```bash
			cd ~/.config/nixpkgs/home.nix
			```
		- Rebuild home-manager
			```bash
			home-manager switch
			```
## Configuration
- Links
	- [Home-Manager Options]
	```bash
	man home-configuration.nix
	```
- Declare user packages
	```nix
	home.packages = with pkgs; [
		firefox
	];
	
	services.dunst = { # if you use a services, you need to manually enble them
		enable = true;
	};
	```
- Applying
	```bash
	home-manager switch
	```
## Dotfiles
- Copy/Symlink
	- Existing config files
		*For exemple, randomly nicked files used by other (who don't use NixOS)*
		```nix
		home.file = {
			".config/alacritty/alacritty.yml".text =  ''
				{"font":{"bold":{"style":"bold"}}}
			'';
		};
		```
		can be done in Home-Manager or in a Nix Modules
		>If not declared and for exeple alacrity gets a big update and the way they set up their yaml file is different or they use another way of configuring this will break
		
	- Stored files (also with no link to NixOS)
		```nix
		home.file.".domm.d" = {
			source ./doom.d; # Where is it
			recurcive = true; # Link any original file or link
			onChange = buildins.readFile ./doom.sh; # if change 
		};
		home.file.".config/polybar/script/mic.sh" = {
			source = ./mic.sh;
			executable = true;
		};
		```
- Declared
	```nix
	{
		xsession = {
			windowManager = {
				baspwm = {
					enable = true;
					rules = {
						"Emacs" = {
							desktop = "3";
							follow = true;
							state = "tiled";
						};
						".blueman-manager-wrapped" = {
							state = "floating";
							sticky = true;
						};
					};
				};
			};
		};
	}
	```
# Flakes
## Introduction
- Flakes is an "upcoming feature" of the Nix package manager.
- Specify code dependencies declaratively (will be stored in flake.lock) // save all core dependencies
	- For exemple: home-manager
- Rebuilding and updating whole system made easy
- Very useful tool to build your own config
	- Multiple configs in one
	- People with github dotfiles will feel right at home
## Getting Started
- [Flakes Wiki]()
- Setup
	- Configuration.nix
		```nix
		nix = {
			package = pkgs.nixFlakes;
			extraOptions = "experimental-features = nix-command flakes"
		};
		```
	- Generate 
		*This command will generate a flake.nix and flake.lock file*
		- pick a location to store in your system `mkdir flake`
		```bash
		nix flake init
		```
	- Inputs and Outputs
		- Inputs
			*attribute set of all the dependecies used in the flake*
			```nix
			inputs = {
				nixpkgs.url = "github:nixos/nixpkgs/nixos-unstable";
			};
			```
		- Outputs
			*function of an argument that uses the inputs for reference*
			- Configure what you imported 
			- Can be pretty much anything: Packages / configurations /modules / etc...
## Configuration
- NixOS
	- Flake.nix
		```nix	
		inputs = {
			nixpkgs.url = "github:nixos/nixpkgs/nixos-unstable";
			#nixpkgs-unstable.url = "github:nixos/nixpkgs/nixospkgs-unstable";
		};
		outputs = { nixpkgs, home-manager, ... }:
			let
				system = "x86_64-linux";
				pkgs = import nixpkgs {
					inherit system;
					config.allowUnfree = true;
				};
				
				lib = nixpkgs.lib;
			in {
				nixosConfigurations = {
					<user> = lib.nixosSystem {
						inherit system;
						modules = [ ./configuration.nix ];
					};
					#<second user> = lib.nixosSystem {
						#inherit system;
						#modules = [ ./configuration.nix ];
					#};
				};
			}
		```
	- Build
		*a ".(#)" will just build host found in location*
		*specify host with ".#<host%>" appended*
		- *optional* `cp /etc/nixos/* <flake location>`
		```bash
		nixos-rebuild build --flake .#
		```
		or
		```bash
		nixos-rebuild switch --flake .#
		```
		
		```bash
		sudo nixos-rebuild switch --flake .#
		```
	- sha256
		```nix
		nixpkgs.overlays = [
			(self: super: {
				discord = super.discord.overrideAttrs (
					_: { src = builtins.fetchTarball {
						url = "https: //discord.com/api/download?platform=linux&format=tar.gz";
						sha256 = "0000000000000000000000000000000000000000000000000000"; # if use flakes 52.0
					}; }
				);
			})
		];
		```
		after rebuild
		```bash
		sudo nixos-rebuild switch --flake .#
		```
		it will display the correct sha256 and should be replace by the 52 0
- Home-Manager
	- Flake.nix
		- Seperate
			```nix
			{
				inputs = {
					...
					home-manager = {
						url = github:nix-community/home-manager;
						inputs.nixpkgs.follows = "nixpkgs";
					};
				};
				outputs = { self, nixpkgs, home-manager, ... }:
					let
						...
					in {
						hmConfig = {
							home-manager.lib.homeManagerConfiguration {
								inherit system pkgs;
								username = "<user>";
								homeDirectory = "/home/<user>";
								#stateVersion = "22.05"; # If there is any complaining about stateVersions, specifically state here.
								configuration = {
									imports = [
										/home/<user>/.config/home/home.nix
									];
								};
							};
						};
					};
			}
			```
		- Inside nixosConfigurations
			```nix
			{
				inputs = {
					...
					home-manager = {
						url = github:nix-community/home-manager;
						inputs.nixpkgs.follows = "nixpkgs";
					};
				};
				outputs = { self, nixpkgs, home-manager, ... }:
					let
						...
					in {
						nixosConfigurations = {
							<user> = lib.nixosSystem {
								inherit system pkgs;
								modules = [
									./configuration.nix
									
									home-manager.nixosModules.home-manager {
										home-manager.useGlobalPkgs = true;
										home-manager.useUserPackages = true;
										home-manager.user.<user> = {
											imports = [ ./home.nix ];
										}; 
									};
								];
							};
						};
					};
			}
			```
	- build
		```bash
		nix build .#hmConfig.<user>.activationPackage
		```
		```bash
		./result/activate
		```
## Updating
*this will update the flake.lock file*
```bash
nix flake update #--recreate-lock-file
```
Now rebuild and switch
## Flake on fresh install
- Boot into ISO
```bash
sudo su
nix-env -iA nixos.git
git clone <repo url> /mnt/<path>
nixos-install --flake .#<host>
reboot
/* login */
sudo rm -r /etc/nixos/configuration.nix
/* move build to desired location */
```
# Personal Config
[Exemple Flake](https://github.com/MatthiasBenaets/nixos-config)
# Resources
## Documentation
1. [NixOS Website](https://nixos.org/)
2. [NixOS Learn](https://nixos.org/learn)
3. [NixOS Manual](https://nixos.org/manual/nixos/stable/)
4. [NixOS Wiki](https://nixos.wiki/wiki/Main_Page)
5. [Nix Pills](https://nixos.org/guides/nix-pills/)
6. [Home-Manager Github](https://github.com/nix-community/home-manager/)
7. [Home-Manager Manual](https://nix-community.github.io/home-manager/)
8. [Home-Manager Appendix A](https://nix-community.github.io/home-manager/options.html)
9. [Home-Manager Appendix B](https://nix-community.github.io/home-manager/nixos-options.html)
10. [List of reference configuration](https://nixos.wiki/wiki/Configuration_Collection)
11. [Exemple Flake](https://github.com/MatthiasBenaets/nixos-config)
12. [options search install](https://search.nixos.org/options)
13. [nix apprentissage from zero](https://zero-to-nix.com/)
## Video
- Best install
![Link Setup guide](https://www.youtube.com/watch?v=AGVXJ-TIv3Y)
- Normal install
![NixOS First Installation](https://www.youtube.com/watch?v=_Z32SYFbxpw)
![move NixOS into a flake](https://www.youtube.com/watch?v=rEovNpg7J0M)
![](https://www.youtube.com/watch?v=61wGzIv12Ds)
![nix game](https://youtu.be/wpS3qIprHL0?si=ssgYnqvWl4oAft13)
![nix host](https://www.youtube.com/watch?v=Cy4X0fjD0-Y)
![server local](https://www.youtube.com/watch?v=DiDm5V_nmzE)