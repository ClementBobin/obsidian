# 🛡️ WSL Cheat-Sheet

This cheat-sheet provides essential commands for managing **Windows Subsystem for Linux (WSL)**, including backing up and restoring distros, symbolic links, file permissions, networking, and running a Linux desktop in WSL2.

---

## 🔍 Overview

- **Product Type**: WSL Management Commands
    
- **Focus**: Key commands for managing WSL distros, symbolic links, networking, and configuring advanced settings.
    

---

## 🧠 Key Commands

### 🔄 Backup and Restore WSL

#### Listing Running Distros

```powershell
wsl --list --verbose
```

#### Starting/Restarting a Distro

```powershell
wsl --distribution DISTRO-NAME
```

#### Terminate a Running Distro

```powershell
wsl --t DISTRO-NAME
```

#### Terminate All Running Distros and WSL Process

```powershell
wsl --shutdown
```

#### Backup a WSL Distro

```powershell
wsl --export (distribution) (filename.tar)
```

#### Restore a WSL Distro from Backup

```powershell
wsl --import (distribution) (install location) (file location and filename)
```

---

### 🔗 Symbolic Links

#### Link .ssh Folder

```bash
sudo ln -s /mnt/c/Users/lempa/.ssh ~/.ssh
```

#### Link .kube Folder

```bash
sudo ln -s /mnt/c/Users/lempa/.kube ~/.kube
```

---

### 🔐 File Permissions

For advanced settings configuration in WSL, refer to [WSL Config Parameters](https://docs.microsoft.com/en-us/windows/wsl/wsl-config).

#### Example `wsl.conf`

```bash
[automount]
enabled = true
options = "metadata,uid=1000,gid=1000,umask=077,fmask=11,case=off"
mountFsTab = true

[interop]
enabled = false
appendWindowsPath = false
```

---

### 🌐 Networking

#### Port Forwarding

**Find IP Address**

```powershell
bash.exe -c "ifconfig eth0 | grep 'inet '"
```

**Add Port Forwarding**

```powershell
$port = 8080
$remoteaddr = 0.0.0.0

netsh interface portproxy add v4tov4 listenport=$port connectport=$port connectaddress=$remoteaddr

netsh advfirewall firewall add rule name=$port dir=in action=allow protocol=TCP localport=$port
```

**Delete Port Forwarding**

```powershell
$port = 8080

netsh interface portproxy delete v4tov4 listenport=$port
netsh advfirewall firewall delete rule name=$port
```

**Show Port Forwardings**

```powershell
netsh interface portproxy show v4tov4
```

---

### 🖥️ Linux Desktop in WSL2

With **WSL2**, it’s possible to install and run a **Linux desktop environment** (such as **XFCE**). A tutorial on how to implement this can be found [here](https://thedatabaseme.de/2022/05/15/shorty-running-xfce-linux-desktop-on-wsl2/).

---

## 📚 Resources

- [WSL Config Parameters](https://docs.microsoft.com/en-us/windows/wsl/wsl-config)
    
- [Running XFCE on WSL2 Tutorial](https://thedatabaseme.de/2022/05/15/shorty-running-xfce-linux-desktop-on-wsl2/)
    

---

## 🔁 Related

- **[Linux on Windows](https://www.example.com/linux-on-windows)** — Learn more about running Linux on Windows with WSL.
    
- **[Networking in WSL](https://www.example.com/wsl-networking)** — Explore more about advanced networking capabilities in WSL.
    

---

## 🔍 Explore More

- **[Advanced WSL Configuration](https://www.example.com/advanced-wsl)** — Deep dive into WSL advanced configuration options.
    
- **[Setting up WSL for Development](https://www.example.com/wsl-dev-setup)** — A step-by-step guide to configure WSL for development.
    

---

## 🏷️ Tags

#wsl  
#backup-restore  
#symbolic-links  
#file-permissions  
#networking  
#port-forwarding  
#linux-desktop  
#wsl2