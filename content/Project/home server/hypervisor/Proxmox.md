# Initialise you're server [[Project/home server/boot|boot]]
# Installation 
## Preprare CD
1. [first you need to download the iso from proxmox VE](https://pve.proxmox.com/wiki/Main_Page)
2. [you need to download Rufus to install the iso on usb](https://rufus.ie/fr/)
>yumi ventoy will not work
3. Download the iso on the usb using Rufus
4. Eject usb when Rufus has finish is programme
## Install proxmox
1. Mount usb on the hardware
2. Launch the hardware
3. boot into the usb
4. Download proxmox graphically
5. follow step:
	- valid 
	- select disk
	- france
	- europe/paris
	- france
	- mot de passe
	- mot de passe
	- email
	- chose internet interface
	- domaine: p310prox.local (exemple)
	- ip addresse: ip/CIDR
	- ip exit réseaux (défault should be you router)
	- ip dns (défault should be you router)*
	- valid
	- wait
6. When download finish, remove usb and restart systeme
7. Connect to the https://ip:8006
## Common problème
### Can't acces internet page
1. verify the rj45 cable, see if the prise is illuminate in your hardware port gbit card
2. verify you're router ip DHCP plage
	- if plage is xxx.xxx.1.10 - xxx.xxx.1.150 and your put your appareil in xxx.xxx.1.250, your hardware cannot be reached
3. add to you're router a IP static ip with the ip you want and the hardware mac adresse for you're network interface 