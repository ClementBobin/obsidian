---
tags:
- cloudnative
- distributedsystems
- helm
- kubernetes
- storage
- volumes
---

# 🐮 Longhorn

> [!info]  
> **Longhorn** is a lightweight, reliable, and easy-to-use distributed block storage system for [[Kubernetes]].  
> It's designed to provide persistent volumes in cloud-native environments.

🔗 **Project Homepage**: [Longhorn Homepage](https://longhorn.io/)  
📚 **Docs**: [Longhorn Docs](https://longhorn.io/docs/)

---

## 🔍 Overview

- **Type**: Cloud-native block storage
    
- **Use Case**: [[Kubernetes]] persistent storage
    
- **Deployment**: #Helm-chart (recommended)
    
- **Key Features**:
    
    - Replication across nodes
        
    - Incremental backups and snapshots
        
    - UI and CLI management
        
    - CRD-based custom resource handling
        

---

## 🛠️ Features

- 🚀 Lightweight and easy to install
    
- 🧱 Supports incremental snapshot and backup
    
- 🔁 Synchronous block-level replication
    
- 🖥️ Built-in UI for volume and backup management
    
- ⚙️ Works with standard Kubernetes volume primitives
    

---

## 🏃 Getting Started

### 📦 Install Longhorn using Helm

> [!tip] Customize [[Helm]] values by reviewing [values.yaml](https://github.com/longhorn/longhorn/blob/master/chart/values.yaml)

```bash
helm repo add longhorn https://charts.longhorn.io
helm repo update
helm install longhorn longhorn/longhorn
```

---

## 🔧 Customization and Configuration

> [!example]+ [[Helm]] Values Example You can override values like storage class name, default replica count, or node selectors in your custom `values.yaml`.

```yaml
defaultSettings:
  defaultReplicaCount: 3
  defaultDataPath: "/var/lib/longhorn"
```

---

## 🛠️ Troubleshooting

> [!question]- Why is my volume stuck in `detached` state?
> 
> - Check if the node is available and has disk space.
>     
> - Look into the `longhorn-manager` logs for possible issues.
>     
> - Ensure the Longhorn UI shows the node as `Ready`.
>     

> [!warning]  
> Make sure **default Kubernetes storage class** is not conflicting with Longhorn if you're using multiple storage providers.

---

## 🔄 Related

- **[[Kubernetes]]** – Container orchestration platform
    
- **[[Helm]]** – Kubernetes package manager
    
- [[Rancher]] – Longhorn is part of the Rancher ecosystem
    

---

## 🌍 Explore More

- 🌐 [Longhorn GitHub](https://github.com/longhorn/longhorn)
    
- 🌐 [Longhorn Troubleshooting](https://longhorn.io/docs/1.5.1/troubleshooting/)
    
- 🌐 [Longhorn UI](https://longhorn.io/docs/1.5.1/references/ui/)
    