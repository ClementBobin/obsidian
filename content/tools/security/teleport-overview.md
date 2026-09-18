---
tags:
- access-control
- cloud
- devsecops
- kubernetes
- security
- ssh
- teleport
---

# 🔐 Teleport

> [!info]  
> **Teleport** is a platform for secure access to #SSH, [[Kubernetes]], #database, internal apps, and more, with #fine-grained-access-controls and #audit-logging. It is designed to address the challenges around access, #DevSecOps, and deploying secure systems at scale.

🌐 **Project Homepage**: [Teleport](https://goteleport.com/)  
📜 **Documentation**: [Teleport Docs](https://goteleport.com/docs/)

---

## 🔍 Overview

> [!info]  
> **Teleport** provides a unified access plane for managing secure access to infrastructure, apps, and databases. It offers enterprise-grade security features and scalability while simplifying user and role management.

### Why Use Teleport?

- **Secure Access**: Centralizes access management for multiple services and resources.
    
- **Audit Logs**: Keeps track of every access request for security and compliance.
    
- **Role-based Access Control ( #RBAC)**: Allows fine-grained control over who can access specific resources.
    
- **Cloud-Native**: Supports dynamic, large-scale environments such as [[Kubernetes]] and #cloud-infrastructure.
    

---

## 🛠️ Features

> [!tip]  
> **Teleport** ensures high security and control over system access:

- 🔑 #SSH **Access**: Secure #SSH access to servers, with automatic session recording.
    
- 🌐 **Kubernetes Access**: Manage access to [[Kubernetes]] clusters without needing to distribute kubeconfigs.
    
- 🧑‍💻 **Database Access**: Securely access #database with strong authentication mechanisms.
    
- 🔒 **Audit Trails**: Keep track of all access requests, ensuring compliance and security.
    
- 🚀 **Cloud Integration**: Easily integrate with #cloud-environments and dynamic infrastructure.
    

---

## 🏃 Getting Started

### 🧑‍💻 Install Teleport

To install Teleport, follow the instructions for your platform on the [Teleport Docs](https://goteleport.com/docs/). For example, on a Linux system:

```sh
curl https://get.gravitational.com/teleport-v7.1.0-linux-amd64-bin.tar.gz -o teleport.tar.gz
tar -xvzf teleport.tar.gz
sudo mv teleport /usr/local/bin/teleport
```

Once installed, you can start Teleport by running:

```sh
teleport start
```

---

## 🔧 Configuration

### 👥 Users and Roles

> [!tip]  
> To manage users and roles in Teleport, refer to the [Role Templates](https://goteleport.com/docs/access-controls/guides/role-templates/) guide.

- **Creating Roles**: Define roles for users to specify the resources they can access and the permissions they have.
    
- **Assigning Roles**: Assign users to specific roles to manage access based on the principle of least privilege.
    

---

### TCTL

To manage nodes and other resources via the command line, Teleport uses `tctl`:

#### 🖥️ Adding Nodes

To add a new node with specific roles, run:

```sh
tctl nodes add --roles=<node,app,kube,proxy,...> --ttl=1h
```

This will add a new node to your Teleport environment with the specified roles.

---

## 🔄 Related

- **[[Kubernetes]]** — Container orchestration platform supported by Teleport.
    
- **[HashiCorp Vault](https://www.vaultproject.io/)** — Secret management tool that can integrate with Teleport for secure access.
    
- **[[Docker]]** — Use Teleport for secure access to [[Docker]] containers and services.
    

---

## 🌍 Explore More

- 🌐 [Teleport Documentation](https://goteleport.com/docs/)
    
- 🌐 [Teleport GitHub Repository](https://github.com/gravitational/teleport)
    