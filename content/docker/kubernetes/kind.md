# 🛠️ Kind Cheat-Sheet

Kind (Kubernetes IN Docker) is a tool to run Kubernetes clusters in Docker containers. It’s perfect for local development or CI/CD pipelines. Kind makes it easy to create multi-node Kubernetes clusters using Docker as the underlying container engine.

- **Official Documentation**: [Kind Quick Start](https://kind.sigs.k8s.io/docs/user/quick-start/)
    

---

## 🔍 Overview

- **Product Type**: Tool for running Kubernetes clusters in Docker containers
    
- **Focus**: Local development and CI/CD pipelines
    
    - **Multi-node clusters**: Create Kubernetes clusters with multiple nodes (control plane and workers)
        
    - **Lightweight**: Runs within Docker containers, making it ideal for resource-constrained environments
        
    - **Integration**: Easily integrates with CI/CD pipelines for Kubernetes testing and development
        
    - **Portability**: Supports running Kubernetes clusters on any machine with Docker installed
        

---

## ⚙️ Installation on Linux

Since Kind uses Docker containers, ensure that Docker is installed and running on your system.

### 📥 Install Kind

To install Kind, download the latest release and move it to `/usr/local/bin`:

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.16.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

---

## 🖱️ Cluster Management

### 🛠️ Cluster Creation

To create a cluster, you need to define a configuration file (`kind-cluster-config.yaml`) that specifies the cluster’s desired nodes and roles. Below is an example configuration:

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: testcluster
# 1 control plane node and 2 workers
nodes:
  - role: control-plane
  - role: worker
  - role: worker
```

#### 🚀 Create the Cluster

Use the following command to create the cluster:

```bash
kind create cluster --config kind-cluster-config.yaml
```

You will see output similar to the following:

```bash
Creating cluster "testcluster" ...
Ensuring node image (kindest/node:v1.25.2)
Preparing nodes
Writing configuration
Starting control-plane
Installing CNI
Installing StorageClass
Joining worker nodes

Set kubectl context to "kind-testcluster"
You can now use your cluster with:
kubectl cluster-info --context kind-testcluster
```

#### 🐳 Check Docker Containers

To check the Docker containers running, use:

```bash
docker ps -a
```

The output will show containers for the control plane and worker nodes:

```bash
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
ac14d8c7a3c9 kindest/node:v1.25.2 "/usr/local/bin/entr..." 2 minutes ago Up About a minute testcluster-worker2
096dd4bf1718 kindest/node:v1.25.2 "/usr/local/bin/entr..." 2 minutes ago Up About a minute 127.0.0.1:42319->6443/tcp testcluster-control-plane
e1ae2d701394 kindest/node:v1.25.2 "/usr/local/bin/entr..." 2 minutes ago Up About a minute testcluster-worker
```

### 🔄 Interacting with Your Cluster

You can have multiple Kind clusters running simultaneously. To list all your Kind clusters, use:

```bash
kind get clusters
```

You will see an output like:

```bash
kind
kind-2
```

#### 🛠️ Set Kubernetes Context

After cluster creation, the context is automatically set to your newly created cluster. You can change contexts using tools like [kubectx](https://github.com/ahmetb/kubectx) or manually set it with the `--context` option in `kubectl`.

### 🗑️ Cluster Deletion

To delete a Kind cluster and its associated kubeconfig, use:

```bash
kind delete cluster -n testcluster
```

The output will show:

```bash
Deleting cluster "testcluster" ...
```

---

## 📝 Further Information

For more tutorials, including how to manage Kind clusters with Ansible, check out:

- [Lightweight Kubernetes Cluster Using Kind and Ansible](https://thedatabaseme.de/2022/04/22/lightweight-kubernetes-cluster-using-kind-and-ansible/)
    

---

## 📚 Resources

- **Official Website**: [Kind Official Site](https://kind.sigs.k8s.io/)
    
- **Documentation**: [Kind Quick Start](https://kind.sigs.k8s.io/docs/user/quick-start/)
    

---

## 🔁 Related

- [**Getting Started with Kubernetes**](https://kubernetes.io/docs/tutorials/kubernetes-basics/) — A guide to setting up and managing Kubernetes clusters.
    
- [**Using Kubernetes with Helm**](https://helm.sh/docs/intro/using_helm/) — Dive deeper into Helm's features for managing Kubernetes applications.
    

---

## 🌍 **Explore More**

- Explore [**Kubernetes Networking**](https://kubernetes.io/docs/concepts/services-networking/) to learn about networking in a containerized environment.
    
- Dive into [**CI/CD Pipelines with Kind**](https://www.redhat.com/sysadmin/kubernetes-kind-pipeline) for integrating Kind in your development and deployment workflows.
    

---

## Tags 📚

#kind #kubernetes #docker #cluster-management #local-development