Here is your **Vagrant Cheat-Sheet** with additional sections included:

---

# 🛡️ Vagrant Cheat-Sheet

Vagrant is an open-source tool for building and maintaining virtualized development environments. It provides a consistent workflow for managing virtual machines (VMs) across multiple platforms. Below is a cheat-sheet with essential Vagrant commands for general management, VM provisioning, and box management.

---

## 🔍 Overview

- **Product Type**: Virtual Machine Management Tool
    
- **Focus**: Streamlining the process of creating and managing reproducible development environments.
    

---

## 🧠 General Management

|COMMAND|DESCRIPTION|
|---|---|
|`vagrant status`|Outputs the status of the current Vagrant machine|
|`vagrant global-status`|Outputs the status of all Vagrant machines|
|`vagrant global-status --prune`|Prunes invalid entries from the global status list|

---

## 🖥️ Managing VMs

|COMMAND|DESCRIPTION|
|---|---|
|`vagrant init`|Initializes Vagrant with a Vagrantfile and `.vagrant` directory (requires specifying a base image in the Vagrantfile before running `vagrant up`)|
|`vagrant up`|Starts the Vagrant environment (provisions only on the first `vagrant up`)|
|`vagrant halt`|Stops the Vagrant machine|
|`vagrant suspend`|Suspends the virtual machine, saving its state|
|`vagrant resume`|Resumes a suspended machine (can also use `vagrant up` for this)|
|`vagrant ssh`|Connects to the machine via SSH|
|`vagrant ssh <BOXNAME>`|SSH into a specific box by name (useful if you have named the box in your `Vagrantfile`)|
|`vagrant destroy`|Stops and deletes the Vagrant machine, removing all traces|
|`vagrant destroy -f`|Same as above, but skips the confirmation prompt|

---

## ⚙️ Provisioning VMs

|COMMAND|DESCRIPTION|
|---|---|
|`vagrant provision`|Forces reprovisioning of the Vagrant machine|
|`vagrant provision --debug`|Enables debug mode for more detailed provisioning output|
|`vagrant up --provision|tee provision.log`|

---

## 📦 Manage Boxes

|COMMAND|DESCRIPTION|
|---|---|
|`vagrant box list`|Lists all installed Vagrant boxes on your computer|
|`vagrant box add <BOXNAME> <BOXURL>`|Downloads and adds a box image to your machine|
|`vagrant box outdated`|Checks for updates for the installed boxes|
|`vagrant box remove <BOXNAME>`|Removes a specific box from the machine|
|`vagrant package`|Packages a running VirtualBox environment into a reusable box|

---

## 🌐 Vagrant with WSL2

Vagrant can also be run inside your **Windows Subsystem for Linux (WSL2)** environment. This allows you to leverage Vagrant's features directly within a Linux-like environment on Windows. For a tutorial on installing and using Vagrant with WSL2 and VirtualBox, check out this [guide](https://thedatabaseme.de/2022/02/20/vagrant-up-running-vagrant-under-wsl2/).

For more advanced usage with **Vagrant and VirtualBox**, refer to the official [Vagrant Documentation](https://www.vagrantup.com/docs).

---

## 🔁 Related

- [[Zero Trust Security]]
    
- [[Cloud Security Posture Management]]
    
- [[XDR]]
    
- [[Firewalls]]
    
- [[SASE]]
    

---

## 🏷️ Tags

#vagrant  
#virtualization  
#dev-environment  
#vm-management  
#wsl2  
#vagrant-boxes  
#provisioning

---

You can explore more Vagrant-related topics here:

- **[Vagrant Basics](https://www.vagrantup.com/docs/getting-started)**: Learn the fundamentals of using Vagrant.
    
- **[Vagrant Boxes](https://www.vagrantup.com/docs/boxes)**: Detailed documentation on working with Vagrant Boxes.
    
- **[Vagrant Provisioning](https://www.vagrantup.com/docs/provisioning)**: A deeper dive into provisioning your VMs with Vagrant.