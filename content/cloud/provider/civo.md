# 🧰 **Civo: Cloud Kubernetes & Instance Management**

> [!info]+  
> **Homepage**: [Civo.com](https://www.civo.com/)  
> **Docs**: [Civo Documentation](https://www.civo.com/docs)  
> **Terraform Provider**: [Civo on Terraform Registry](https://registry.terraform.io/providers/civo/civo/latest)

---

## 🚀 **Civo CLI**

Civo CLI is a powerful command-line tool to manage your Civo resources directly from the terminal. It is built with Go and distributed as cross-platform binaries via [GitHub Releases](https://github.com/civo/cli/releases).

---

### 🔐 **Authentication**

To use the CLI, you’ll need to authenticate via an API key.

> [!tip] **Get your API key**  
> Visit [https://www.civo.com/api](https://www.civo.com/api) to find or regenerate your API key.

---

### 🛠️ **Create an Instance**

You can quickly create instances using the `civo instance create` command.

```bash
civo instance create --hostname=<your-hostname> \
  --sshkey=<your-ssh-key-name> \
  --initialuser=xcad \
  --size=g3.xsmall \
  --diskimage=921fcb64-8abf-4a51-8823-027d9d75c1d4
```

> [!example] **Quick Setup**  
> Replace `<your-hostname>` and `<your-ssh-key-name>` with your values. You can customize the size, disk image, and user.

---

### ⚙️ **CLI Parameters Table**

|Short|Long|Description|
|---|---|---|
|`-t`|`--diskimage`|Disk image to use (`civo diskimage ls`)|
|`-l`|`--firewall`|Firewall (name or ID)|
|`-s`|`--hostname`|Instance hostname|
|`-u`|`--initialuser`|Initial user for the instance|
|`-r`|`--network`|Network (name or ID)|
|`-p`|`--publicip`|Either `"none"` or `"create"` (default)|
|`-i`|`--size`|Size (`civo instance size`)|
|`-k`|`--sshkey`|SSH key (name or ID)|
|`-g`|`--tags`|Tags to attach to the instance|
|`-w`|`--wait`|Wait for the instance to be ready|

---

## 📏 **Available Instance Sizes**

> [!note] **Type Definitions**  
> `Instance` types are for general compute. `Kubernetes` types are optimized for K3s clusters.

|ID|Label|Type|CPU|RAM (MB)|SSD (GB)|
|---|---|---|---|---|---|
|g3.xsmall|ExtraSmall|Instance|1|1024|25|
|g3.small|Small|Instance|1|2048|25|
|g3.medium|Medium|Instance|2|4096|50|
|g3.large|Large|Instance|4|8192|100|
|g3.xlarge|ExtraLarge|Instance|6|16384|150|
|g3.2xlarge|2XLarge|Instance|8|32768|200|
|g3.k3s.xsmall|ExtraSmall|Kubernetes|1|1024|15|
|g3.k3s.small|Small|Kubernetes|1|2048|15|
|g3.k3s.medium|Medium|Kubernetes|2|4096|15|
|g3.k3s.large|Large|Kubernetes|4|8192|15|
|g3.k3s.xlarge|ExtraLarge|Kubernetes|6|16384|15|
|g3.k3s.2xlarge|2XLarge|Kubernetes|8|32768|15|

---

## 💽 **Available Disk Images**

Use `civo diskimage ls` to list available disk images, or refer to these popular options:

|ID|Name|
|---|---|
|`9ffb043e-37d8-4b71-80ed-81227564944f`|centos-7|
|`e1a83a29-d35b-433b-b1cb-4baade48c81a`|debian-10|
|`67a75d21-3726-4152-8fc9-dcdb51b6e39e`|debian-9|
|`880d37ca-372e-4d33-91bd-3122cf56614b`|ubuntu-bionic|
|`921fcb64-8abf-4a51-8823-027d9d75c1d4`|ubuntu-focal|

---

## 📚 **Related**

- [Civo Kubernetes Quickstart Guide](https://www.civo.com/learn)
    
- [Civo CLI GitHub Repo](https://github.com/civo/cli)
    
- [Civo Academy - Learn Cloud with Civo](https://www.civo.com/learn)
    

---

## 🧳 **Explore More 🌍**

- [Terraform Civo Provider Docs](https://registry.terraform.io/providers/civo/civo/latest/docs)
    
- [Civo GitHub Examples](https://github.com/civo)
    

---

## 🏷️ **Tags 📚**

#civo  
#kubernetes  
#cloud  
#infrastructure  
#cli  
#terraform  
#devops  
#instance-management