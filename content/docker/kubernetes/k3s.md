# 🪶 K3S Cheat-Sheet

K3S is a lightweight Kubernetes distribution designed for IoT and edge computing environments. It’s production-ready and easy to install with a binary size under 100 MB, consuming less memory compared to traditional Kubernetes setups.

- **Project Homepage**: [K3s.io](https://www.k3s.io/)
    
- **Documentation**: [K3s Documentation](https://docs.k3s.io/)
    

---

## 🔍 Overview

- **Product Type**: Lightweight Kubernetes Distribution
    
- **Focus**: K3S is tailored for environments that need a small footprint and minimal resource consumption, such as **IoT**, **edge computing**, and small clusters.
    
    - **Single-Node Setup**: Ideal for development and testing
        
    - **Multi-Node Setup**: High Availability (HA) configurations with embedded or external databases
        
    - **Ease of Installation**: Simple and quick installation with automated scripts
        

---

## 🔧 Installation

You can install K3S using several methods: with an **external database**, **embedded database**, or as a **single-node** setup.

### 📊 K3s with External DB

Set up a High Availability (HA) K3s cluster backed by an external database like MySQL, PostgreSQL, or etcd.

#### 🗃️ Install Database

- First, install [MariaDB](https://chatgpt.com/c/databases/mariadb.md) or your preferred database.
    

#### 🖥️ Install Servers

To install K3s with an external database:

```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--datastore-endpoint='mysql://user:pass@tcp(ipaddress:3306)/dbname' \
--node-taint CriticalAddonsOnly=true:NoExecute \
--tls-san your-dns-name --tls-san your-lb-ip-address
```

> [!info]  
> The `--node-taint` flag ensures that your server node won’t run workloads, only the control plane.

#### 🔒 SSL Certificates

To avoid certificate errors, you should use the `--tls-san YOUR_IP_OR_HOSTNAME_HERE` option to add extra IPs or hostnames to the TLS certificate.

#### 🚀 Install Agents

You can install agents on additional nodes:

```bash
curl -sfL https://get.k3s.io | sh -s - agent \
--server https://your-lb-ip-address:6443 \
--token YOUR-SECRET
```

---

### 💾 K3s with Embedded DB

Set up an HA K3s cluster using K3s's built-in distributed database (etcd).

#### 🖥️ Install the First Server

```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--tls-san your-dns-name --tls-san your-lb-ip-address \
--cluster-init
```

> [!tip]  
> The `--tls-san` option ensures no SSL certificate errors when accessing the server via IP or hostname.

#### 🏗️ Install Additional Servers

To add more servers:

```bash
curl -sfL https://get.k3s.io | sh -s - server \
--token=YOUR-SECRET \
--tls-san your-dns-name --tls-san your-lb-ip-address \
--server https://IP-OF-THE-FIRST-SERVER:6443
```

The `--cluster-init` option initializes the HA cluster with an embedded etcd database. You need at least 3 nodes for fault tolerance.

#### 🗓️ Fault Tolerance Table

|Total Number of Nodes|Failed Node Tolerance|
|---|---|
|1|0|
|2|0|
|3|1|
|4|1|
|5|2|
|6|2|

#### 🖥️ Install Agents

To install agent nodes:

```bash
curl -sfL https://get.k3s.io | sh -s - agent \
--server https://your-lb-ip-address:6443 \
--token YOUR-SECRET
```

---

### ⚙️ K3s Single Node

Set up K3s as a single-node installation.

> [!warning]  
> This setup is ideal for testing and development but may not be suitable for production.

---

## 🛠️ Manage K3S

### 💻 Management on Server Nodes

Use the K3S-specific `kubectl` to manage your cluster:

```bash
k3s kubectl
```

### 📜 Download Kube Config

You can download the kubeconfig file from:

```
/etc/rancher/k3s/k3s.yaml
```

---

## 💾 Database Backups

### 🧳 etcd Snapshots

K3S stores etcd snapshots in the following directory:

```
/var/lib/rancher/k3s/server/db/snapshots
```

> [!tip]  
> Regular backups of the etcd database are crucial for disaster recovery.

---

## 📚 Resources

- **Official Website**: [K3s Official Website](https://www.k3s.io/)
    
- **Documentation**: [K3s Documentation](https://docs.k3s.io/)
    

---

## 🔁 Related

- [**Getting Started with Kubernetes**](https://kubernetes.io/docs/tutorials/kubernetes-basics/) — A guide to setting up and managing Kubernetes clusters.
    
- [**Using Kubernetes with Helm**](https://helm.sh/docs/intro/using_helm/) — Dive deeper into Helm's features for managing Kubernetes applications.
    

---

## 🌍 **Explore More**

- Explore [**Kubernetes Networking**](https://kubernetes.io/docs/concepts/services-networking/) to learn about networking in a containerized environment.
    
- Dive into [**K3s Troubleshooting**](https://rancher.com/docs/k3s/latest/en/troubleshooting/) for advanced troubleshooting techniques when managing your K3s clusters.
    

---

## Tags 📚

#k3s #kubernetes #cluster #high-availability #lightweight #edge-computing