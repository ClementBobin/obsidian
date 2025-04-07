# 🚢 Portainer

> [!info]  
> **Portainer** makes it easy to deploy, configure, and secure containers in minutes on [[Docker]], [[Kubernetes]], [[Swarm]], and [[Nomad]], across any cloud, datacenter, or device.

🌐 **Project Homepage**: [Portainer Homepage](https://www.portainer.io/)  
📚 **Documentation**: [Portainer Docs](http://documentation.portainer.io/)

---

## 🔍 Overview

> [!info]  
> **Portainer** is a powerful #container-management tool that simplifies #container-orchestration on platforms like [[Docker]], [[Kubernetes]], [[Swarm]], and [[Nomad]]. With a simple user interface, it provides full control over the deployment, configuration, and security of #containers.

### Why Use Portainer?

- #Multi-Platform **Support**: Manage containers across [[Docker]], [[Kubernetes]], [[Swarm]], and [[Nomad]].
    
- **Easy-to-Use Interface**: Intuitive #GUI for managing complex containerized environments.
    
- **Secure Container Management**: Provides #role-based #access-control ( #RBAC) for teams and organizations.
    
- **Quick Setup**: Easily #deploy and configure #containers with minimal effort.
    
- #Cloud **and #Datacenter Support**: Works in any #cloud, #datacenter, or #on-premise environment.
    

---

## 🛠️ Features

> [!tip]  
> **Portainer** simplifies managing your #containers with the following features:

- 🔒 #Role-Based #Access-Control ( #RBAC)**: Secure your environment with detailed user permissions.
    
- 🌍 #Cross-Platform **Management**: Works with [[Docker]], [[Kubernetes]], [[Swarm]], and [[Nomad]].
    
- 🖥️ **Web-Based Interface**: Easy-to-use #GUI for managing #containers, #services, and #networks.
    
- 🔄 **Container Deployment**: Quickly #deploy and configure #containers with minimal setup.
    
- 📊 **Real-Time Monitoring**: View container #logs, performance, and statistics in real-time.
    

---

## 🏃 Getting Started

### 🧑‍💻 Install Portainer

To deploy Portainer using [[Docker]], run the following command:

```sh
docker volume create portainer_data
docker run -d -p 9000:9000 --name portainer \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data portainer/portainer-ce
```

> [!tip]  
> Portainer will be accessible via `http://localhost:9000` once the container is up.

---

## 🔧 Basic Usage

### Access the Web Interface

To access Portainer’s web interface, navigate to:

```
http://<your-server-ip>:9000
```

### Connect to [[Docker]]

After logging in, you can manage [[Docker]] by selecting the **[[Docker]]** environment and start configuring your containers.

### Deploy a New Container

To deploy a container through Portainer’s interface, click on **Containers** and then **Add container**.

### Manage Volumes and Networks

You can manage #Docker-volumes and networks via the #Volumes and #Networks sections in the web interface.

---

## 🔄 Related

- **[[Docker]]** — The platform used for creating, deploying, and running #containers.
    
- **[[Kubernetes]]** — A #container-orchestration platform that can be managed with Portainer.
    
- **[[Nomad]]** — A #cluster manager and scheduler from #HashiCorp, supported by Portainer.
    

---

## 🌍 Explore More

- 🌐 [Portainer Documentation](http://documentation.portainer.io/)
    
- 🌐 [Portainer GitHub Repository](https://github.com/portainer/portainer)
    

---

## 📚 Tags

- #Portainer
    
- #Docker
    
- #Kubernetes
    
- #Swarm
    
- #ContainerManagement
    
- #Security
    
- #Orchestration
    