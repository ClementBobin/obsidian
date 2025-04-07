# OpenSSH Cheat-Sheet

OpenSSH is a suite of secure networking utilities based on the Secure Shell (SSH) protocol. It provides a secure way to access remote systems, transfer files, and perform various tasks.

---

## 🔑 Known Hosts

### Remove Entry from the Known-Hosts File

To remove an entry from your known hosts file (e.g., when a server’s key changes or you no longer need to connect to a host), run:

```bash
ssh-keygen -R hostname
```

This command removes the specified host's entry from the `~/.ssh/known_hosts` file.

---

## ⚙️ Using the SSH Config File

If you are regularly connecting to multiple remote systems over SSH, you can configure your remote servers in the `~/.ssh/config` file. This allows for simpler and more customized SSH connections.

### Example `.ssh/config` File

```ini
Host dev     
	HostName dev.your-domain     
	User xcad     
	Port 7654     
	IdentityFile ~/.ssh/targaryen.key  
	Host *     
	User root     
	Compression yes
```

- **Host**: The alias for your SSH connection.
    
- **HostName**: The actual hostname or IP address of the remote server.
    
- **User**: The username to log in with.
    
- **Port**: The port to use for the connection (default is 22).
    
- **IdentityFile**: The path to your SSH private key for authentication.
    
- **Compression**: Enables compression during the SSH session (optional).
    

You can now connect to the `dev` host by simply running:

```bash
ssh dev
```

---

## 🖥️ Related

- **[SSH Protocol](https://en.wikipedia.org/wiki/Secure_Shell)**: Learn about the Secure Shell (SSH) protocol and its uses for secure communication between devices.
    
- **SCP (Secure Copy Protocol)**: A protocol to securely transfer files between hosts using SSH. Often used in conjunction with SSH for remote file management.
    
- **SSH Keys**: Using public and private SSH keys to authenticate and establish secure connections.
    

---

## 🔍 Explore More

- **OpenSSH Official Documentation**: Official manual for OpenSSH with more detailed explanations of SSH commands and configuration.
    
- **SSH Config File Examples**: Learn more advanced configurations and tips for setting up your `.ssh/config` file.
    
- **Troubleshooting SSH**: A guide to solving common SSH connection issues and errors.
    

---

## 🏷️ Tags

#ssh #openssh #ssh-config #networking #remote-access #security #linux

---

## 📚 Resources

- **[OpenSSH GitHub Repository](https://github.com/openssh/openssh-portable)**: Access the source code for OpenSSH and contribute.
    
- **SSH Cheat Sheet**: A quick reference guide for SSH commands and configurations.
    
- **DigitalOcean SSH Guide**: A beginner-friendly guide to SSH keys and their usage for secure logins.