# Packer

Packer is a tool for creating identical machine images for multiple platforms from a single source configuration. It simplifies the process of building consistent, reproducible, and automated machine images for various cloud environments, virtual machines, and other platforms.

- **Project Homepage**: [Packer](https://www.packer.io)
    
- **Documentation**: [Packer Docs](https://developer.hashicorp.com/packer/docs)
    
- **Plugins**: [Packer Plugins](https://developer.hashicorp.com/packer/plugins)
    

---

## 🛠️ Installation

### macOS

To install Packer on macOS, use the Homebrew package manager:

```bash
brew tap hashicorp/tap brew install hashicorp/tap/packer
```

### Windows

For Windows, download and install Packer from the official website:

- **[Download Packer for Windows](https://developer.hashicorp.com/packer/downloads)**
    

### Linux

#### Ubuntu/Debian

To install Packer on Ubuntu or Debian-based distributions, follow these steps:

1. Add HashiCorp's GPG key:
    
    ```bash
    wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
    ```
    
2. Add the Packer repository to your system:
    
    ```bash
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
    ```
    
3. Install Packer:

    ```bash
    sudo apt update && sudo apt install packer
    ```
    

---

## 🔌 Plugins

Packer supports a wide range of plugins to extend its functionality, allowing you to create machine images for different platforms.

### Proxmox Builder

The [Proxmox](infra/proxmox.md) Packer builder enables you to create virtual machines and store them as new images. It includes two types of builders:

- [proxmox-clone](https://developer.hashicorp.com/packer/plugins/builders/proxmox/clone): Clone existing virtual machines.
    
- [proxmox-iso](https://developer.hashicorp.com/packer/plugins/builders/proxmox/iso): Create VMs from ISO files.
    

#### Authentication

You can authenticate to **Proxmox** using the following environment variables:

- `PROXMOX_URL`
    
- `PROXMOX_USERNAME`
    
- `PROXMOX_PASSWORD`
    
- `PROXMOX_TOKEN`
    

See the [Proxmox Authentication Guide](infra/proxmox.md) for more details.

#### Example Template

Here is a basic example of a Proxmox builder template (Work In Progress - WIP):

```ini
# Packer Template for Proxmox builder "proxmox-iso" 
{   
	iso_url = "http://example.com/ubuntu.iso"   
	iso_checksum = "sha256:abc123..."   
	vm_name + "ubuntu-template"   
	os_type = "ubuntu"   
	cpus = 2   
	memory = 4096   
	disk_size = 10240    
	# Additional Proxmox-specific settings go here 
}
```

---

## 🏆 Key Features

- **Multi-Platform Support**: Create identical machine images for various platforms (AWS, Azure, VMware, VirtualBox, etc.).
    
- **Automated Image Building**: Streamline the process of building and deploying infrastructure.
    
- **Customizable Templates**: Use JSON or HCL templates to configure machine images.
    
- **Extensible Plugin System**: Support for a wide variety of cloud and virtualization platforms.
    

---

## 🔗 Related

- **[Terraform](https://www.terraform.io/)**: Use Packer in conjunction with Terraform to provision infrastructure and deploy machine images.
    
- **[Ansible](https://www.ansible.com/)**: Automate configuration management and software provisioning with Ansible, often used alongside Packer.
    
- **[Vagrant](https://www.vagrantup.com/)**: A tool for managing virtual machines for development, which works well with Packer to provision environments.
    

---

## 🔍 Explore More

- **Packer Templates**: Learn how to create and manage machine image templates.
    
- **Packer Provisioners**: Automate software installation and configuration during the image creation process.
    
- **Packer on AWS**: Use Packer with AWS to create AMIs (Amazon Machine Images).
    

---

## 🏷️ Tags

#packer #infrastructure-as-code #virtualization #automation #cloud #machine-images #provisioning

---

## 📚 Resources

- **[Packer Documentation](https://developer.hashicorp.com/packer/docs/)**: Comprehensive documentation for installation, configuration, and usage.
    
- **[Packer GitHub Repository](https://github.com/hashicorp/packer)**: Access the source code and contribute to the Packer project.
    
- **[Packer Examples](https://github.com/hashicorp/packer-examples)**: A collection of example Packer templates for various use cases.