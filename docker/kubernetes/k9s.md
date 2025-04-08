# 🐾 K9s Cheat-Sheet

K9s is a command-line interface designed to simplify managing [Kubernetes Clusters](https://chatgpt.com/c/kubernetes.md). It allows you to interact with clusters in an efficient way, making tasks like editing resource manifests, shelling into pods, and managing multiple clusters easier.

- **More Information & Releases**: [K9s GitHub Repository](https://github.com/derailed/k9s)
    

---

## 🔍 Overview

- **Product Type**: Command-Line Interface (CLI) for Kubernetes Management
    
- **Focus**: Simplifying interaction with Kubernetes clusters by providing easy access to resources and quick actions for managing pods, services, and other Kubernetes components.
    
    - **Resource Management**: Efficiently manage and interact with Kubernetes resources (pods, services, etc.)
        
    - **Multiple Clusters**: Switch between multiple clusters quickly
        
    - **Interactive Interface**: Use keyboard shortcuts for seamless operation
        
    - **Logs and Shelling**: Easily view logs or shell into containers
        

---

## ⚙️ Installation

### 📦 On Linux

#### 🔍 Find and Download the Latest Release

Visit the [release page](https://github.com/derailed/k9s/releases), choose the appropriate package (e.g., Linux_x86_64), and copy the download link. Use the following commands to download and unpack the archive:

```bash
wget https://github.com/derailed/k9s/releases/download/v0.26.6/k9s_Linux_x86_64.tar.gz
tar -xvf k9s_Linux_x86.tar.gz
```

#### 🛠️ Install K9s

```bash
sudo install -o root -g root -m 0755 k9s /usr/local/bin/k9s
```

---

## 🖱️ Commands

### 🌐 Cluster Selection

Once K9s is running, you can change the cluster by typing `:context`. A list of available configurations appears. Use the arrow keys to select the desired cluster and press enter.

### 📝 General Command Structure

#### 📜 Menu

You can switch between resource types by pressing `:`. Then, type the resource type (e.g., `pod`, `services`) and press enter to confirm.

#### 👀 Selection

Selections are made using the arrow keys. After selecting a resource, press enter to drill down and view more details (e.g., view running containers inside a pod).

#### 🔍 Filter & Searches

In almost every K9s screen, you can apply filters or search by pressing `/` and entering your search term. Press enter to apply the filter or search. Some screens allow namespace filtering using number keys, where `0` shows all namespaces.

---

### ⏩ Useful Shortcuts and Commands

|Command|Description|Comparable kubectl Command|
|---|---|---|
|`:pod`|Switch to the pod screen to view all pods in the current cluster.|`kubectl get pods --all-namespaces`|
|`:services`|Switch to the service screen to view all services.|`kubectl get services --all-namespaces`|
|`ctrl`+`d`|Delete a resource.|`kubectl delete <resource> -n <namespace>`|
|`ctrl`+`k`|Kill a resource (no confirmation).||
|`s`|On the Pod screen, open a shell into the selected pod.|`kubectl exec -n <namespace> <pod_name> -c <container_name> -- /bin/bash`|
|`l`|Show the log output of a pod.|`kubectl logs -n <namespace> <pod_name>`|

---

## 📚 Resources

- **Official Website**: [K9s GitHub Repository](https://github.com/derailed/k9s)
    
- **Documentation**: [K9s Wiki](https://github.com/derailed/k9s/wiki)
    

---

## 🔁 Related

- [**Getting Started with Kubernetes**](https://kubernetes.io/docs/tutorials/kubernetes-basics/) — A guide to setting up and managing Kubernetes clusters.
    
- [**Using Kubernetes with Helm**](https://helm.sh/docs/intro/using_helm/) — Dive deeper into Helm's features for managing Kubernetes applications.
    

---

## 🌍 **Explore More**

- Explore [**Kubernetes Networking**](https://kubernetes.io/docs/concepts/services-networking/) to learn about networking in a containerized environment.
    
- Dive into [**K9s Troubleshooting**](https://github.com/derailed/k9s/wiki/FAQ) for advanced troubleshooting techniques when managing your K9s clusters.
    

---

## Tags 📚

#k9s #kubernetes #CLI #kubectl-alternative #container-management