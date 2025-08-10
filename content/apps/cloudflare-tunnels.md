# 🌐 Cloudflare Tunnel Setup Guide

## 🔍 Overview

> [!info]  
> **Cloudflare Tunnel** is a service that provides secure access to web applications, protecting your servers from direct attacks. This solution helps avoid complex network setups and eliminates the need for traditional [[ACL]]s and [[GRE tunnel]]s. It's ideal for protecting applications running in any environment, whether in the public cloud, private cloud, Kubernetes clusters, or even a local server.

---

## 🛠️ Installing Cloudflare Tunnel

### Step 1: Download and Install the Cloudflare Tunnel Service

> [!tip]  
> On your Ubuntu machine, run the following command to download and install the Cloudflare Tunnel service:

```bash
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb && sudo dpkg -i cloudflared-linux-amd64.deb
```

🌍 **Explore More**: Learn more about Cloudflare Tunnel installation options for other systems on [Cloudflare Tunnel Docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/).

### Step 2: Login to Cloudflare

> [!info]  
> After installing, use the following command to log in to your Cloudflare account:

```bash
cloudflared tunnel login
```

You will be prompted to visit a URL in your browser and log in to Cloudflare. After logging in, Cloudflare will provide you with a `cert.pem` file. Make sure to note the location of this file, as you will need it in subsequent steps.

🌍 **Explore More**: Cloudflare login options and troubleshooting can be found on [Cloudflare CLI Documentation](https://github.com/cloudflare/cloudflared/blob/master/README.md).

---

## 🚀 Creating a Tunnel

### Step 3: Create a Tunnel

> [!warning]  
> To create a new tunnel, run the following command:

```bash
cloudflared tunnel create <NAME>
```

Replace `<NAME>` with the name you want to assign to your tunnel. After running this command, make a note of where Cloudflare saves your tunnel credentials.

🌍 **Explore More**: For an in-depth guide on creating and managing tunnels, visit [Cloudflare Tunnels Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/).

---

## ⚙️ Configuring the Tunnel

### Step 4: Create the Configuration File

> [!tip]  
> Create a configuration file for your tunnel in the `.cloudflared` directory:

```bash
nano /home/$USER/.cloudflared/config.yaml
```

Inside the `config.yaml` file, add the following lines:

```yaml
tunnel: Your-Tunnel-Id
credentials-file: /home/$USER/.cloudflared/1d4537b6-67b9-4c75-a022-ce805acd5c0a.json
```

Make sure to replace `Your-Tunnel-Id` with your actual tunnel ID. The `credentials-file` path should point to the JSON file you received earlier in the process.

🌍 **Explore More**: Check out more configuration options on the [Cloudflare Tunnel Configuration Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/configuration/).

### Step 5: Add Your First Site

> [!note]  
> To route traffic to your site (e.g., `example.com`), run the following command:

```bash
cloudflared tunnel route dns <name of the tunnel> <example.com>
```

This command associates your tunnel with the [[DNS]] record `example.com`.

🌍 **Explore More**: Learn about [[DNS]] routing and configurations from the [Cloudflare DNS Documentation](https://developers.cloudflare.com/dns/).

---

## 🔄 Setting Up Ingress

### Step 6: Create an Ingress File

> [!tip]  
> Create a file named `config.yml` in the `.cloudflared` directory:

```bash
nano /home/$USER/.cloudflared/config.yml
```

In this file, define the ingress rules as follows:

```yaml
ingress:
  - hostname: example.com
    service: http://internalip:80
  - hostname: sub.example.com
    service: http://internalip:88
  - service: http_status:404 # This is required as a 'catch-all'
```

Replace `example.com` with your actual domain and `internalip` with the internal [[IP]] address of your server.

🌍 **Explore More**: For detailed information on ingress configuration, check out [Cloudflare Ingress Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/ingress/).

---

## 🏃 Running the Tunnel

### Step 7: Start the Tunnel

> [!warning]  
> To start the tunnel, run the following command:

```bash
cloudflared tunnel run <name of your tunnel>
```

Replace `<name of your tunnel>` with the name you assigned earlier.

🌍 **Explore More**: Learn about running Cloudflare Tunnel in production from the [Cloudflare Tunnel Runtime Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/running-tunnel/).

---

## 🗃️ Running the Tunnel as a Service

### Step 8: Create a Service for Auto-Start

> [!info]  
> To ensure that the tunnel starts automatically with your machine, install Cloudflare as a service:

```bash
cloudflared service install
```

🌍 **Explore More**: For more about managing Cloudflare Tunnel as a service, visit [Cloudflare Tunnel Service Installation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/service-installation/).

### Step 9: Enable and Start the Service

> [!tip]  
> Enable the Cloudflare Tunnel service to start on boot and start it immediately:

```bash
systemctl enable --now cloudflared
```

🌍 **Explore More**: For more service management commands, refer to [Systemd Service Management](https://www.freedesktop.org/wiki/Software/systemd/).

---

## 🔧 Troubleshooting and Additional Notes

> [!warning]
> 
> - **Ensure {{DNS}} propagation**: If your tunnel does not work immediately, verify [[DNS]] settings and propagation.
>     
> - **Check [[firewall]] settings**: Ensure your [[firewall]] allows traffic on the relevant ports for your services.
>     
> - **Monitor the tunnel**: Use `cloudflared logs` to view [[log]]s if issues arise with your tunnel.
>     

🌍 **Explore More**: For troubleshooting tips, visit [Cloudflare Troubleshooting Guide](https://developers.cloudflare.com/cloudflare-one/troubleshooting/).

---

## 🔁 Related

> [!info]
> 
> - **[Network Protocols and Analysis Tools](https://www.example.com/protocols-tools)** — Discover more about network protocol analyzers and other tools available for network analysis.
>     
> - **[Network Security and Intrusion Detection](https://www.example.com/security-intrusion-detection)** — Learn more about network security best practices and intrusion detection systems.
>     
> - **[Zero Trust Architecture](https://www.example.com/zero-trust)** — Explore the concept of Zero Trust in network security and how it enhances application protection.
>     
> - **[Cloudflare Security Features](https://www.example.com/cloudflare-security)** — Learn about Cloudflare’s advanced security features for enhanced protection of web applications.
>     

---

## 🔗 Further Resources

For additional details and advanced configurations, visit the official Cloudflare Tunnel documentation:

- [Cloudflare Tunnel Docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)
    
- [Cloudflare CLI Reference](https://github.com/cloudflare/cloudflared/blob/master/README.md)
    
- [Cloudflare DNS Documentation](https://developers.cloudflare.com/dns/)
    
- [Cloudflare Tunnel Configuration Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/configuration/)
    
- [Cloudflare Ingress Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/ingress/)
    
- [Cloudflare Tunnel Runtime Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/running-tunnel/)
    
- [Cloudflare Tunnel Service Installation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/service-installation/)
    
- [Systemd Service Management](https://www.freedesktop.org/wiki/Software/systemd/)
    
- [Cloudflare Troubleshooting Guide](https://developers.cloudflare.com/cloudflare-one/troubleshooting/)
    

---

## 📚 Tags:

#Cloudflare  
#Tunnel  
#SSL  
#DNS  
#Ingress  
#Kubernetes  
#CLI  
#Security