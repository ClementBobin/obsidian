---
tags:
- remote-access
- secure-networking
- tailscale
- vpn
- wireguard
---

# 🛡️ Tailscale

> [!info]  
> **Tailscale** is a zero-configuration [[VPN]] that makes it easy to create secure #network. Powered by [[WireGuard]], [[Tailscale]] can be installed on any device in minutes, offering remote access from any network or physical location.

🌐 **Project Homepage**: [Tailscale](https://tailscale.com/)

---

## 🔍 Overview

> [!info]  
> **Tailscale** leverages [[WireGuard]] to create a secure mesh #network, offering private connectivity between devices without complicated setup or configuration.

### Why Use Tailscale?

- **Zero Configuration**: Install and use with no need for complicated setup or networking expertise.
    
- **Security**: Uses [[WireGuard]], a modern [[VPN]] protocol known for its security and performance.
    
- **Remote Access**: Connect securely from any device, no matter the network or physical location.
    
- **Cross-Platform**: Supports a wide variety of devices, including laptops, smartphones, and [[IoT]] devices.
    
- **Ease of Use**: Simple installation process that takes minutes to set up.
    

---

## 🛠️ Features

> [!tip]  
> **Tailscale** offers an easy and secure solution for private #networking:

- 🔐 **Zero-Trust Network**: Ensures devices can communicate without requiring a central [[VPN]] server.
    
- 🔄 **Seamless Device Access**: Access any device connected to the network from anywhere.
    
- 🚀 **Fast Setup**: Installs in minutes with minimal configuration.
    
- 📱 **Cross-Device Support**: Works on [[Window]]s, [[MacOS]], [[Linux]], [[iOS]], and [[Android]].
    
- 🖧 **Private [[DNS]]**: Tailscale automatically sets up private DNS to simplify access across devices.
    

---

## 🏃 Getting Started

### 🧑‍💻 Install Tailscale

To install Tailscale on your device, follow the instructions for your platform on the [Tailscale Docs](https://tailscale.com/kb/).

For example, on a [[Linux]] system, use the following:

```sh
curl -fsSL https://tailscale.com/install.sh | sh
```

Once installed, log in using your [[Google]], [[Microsoft]], or [[GitHub]] account:

```sh
sudo tailscale up
```

---

## 🔧 Configuration

Tailscale automatically configures a mesh #network once connected. To see connected devices, run:

```sh
tailscale status
```

> [!tip]  
> To add devices, simply install Tailscale on any other device and log in using the same account.

---

## 🔄 Related

- **[[WireGuard]]** — The [[VPN]] protocol powering Tailscale.
    
- **[[Docker]]** — Run Tailscale in [[Docker]] for secure, isolated environments.
    
- **[[Cloudflare]]** — Secure tunneling services that can complement Tailscale’s [[VPN]].
    

---

## 🌍 Explore More

- 🌐 [Tailscale Documentation](https://tailscale.com/kb/)
    
- 🌐 [Tailscale GitHub Repository](https://github.com/tailscale/tailscale)
    
