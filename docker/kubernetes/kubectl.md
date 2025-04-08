# 🛠️ Kubectl Cheat-Sheet

Kubectl is the command line tool to interact with a [Kubernetes Cluster](https://chatgpt.com/c/kubernetes.md)'s control plane using the Kubernetes API.

- **Official Documentation:** [Kubectl Reference](https://kubernetes.io/docs/reference/kubectl/)
    

---

## ⚙️ Installation

### 📦 On Windows (PowerShell)

Install `kubectl` using [chocolatey](https://chatgpt.com/c/tools/chocolatey.md):

```bash
choco install kubernetes-cli
```

### 📥 On Linux

> [!INFO] **Installing on WSL2**  
> On WSL2, it's recommended to install Docker Desktop [docker-desktop](https://www.docker.com/products/docker-desktop/), which includes kubectl.

#### Download the Latest Release

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"  
```

#### Install kubectl

```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

### 🍏 On macOS

Install `kubectl` using [homebrew](https://chatgpt.com/c/tools/homebrew.md):

```zsh
brew install kubernetes-cli
```

---

## ⚙️ Config Management

### 📂 Multiple Config Files

#### On Windows (PowerShell)

```powershell
$env:KUBECONFIG = "$HOME/.kube/prod-k8s-clcreative-kubeconfig.yaml;$HOME/.kube/infra-home-kube-prod-1.yml;$HOME/.kube/infra-home-kube-demo-1.yml;$HOME/.kube/infra-cloud-kube-prod-1.yml"
```

#### On Linux

```bash
export KUBECONFIG=~/.kube/kube-config-1.yml:~/.kube/kube-config-2.yml
```

You can automate adding multiple kubeconfigs to the `KUBECONFIG` environment variable with the following script. Add it to your shell rc file (e.g., `.bashrc` or `.zshrc`):

```bash
# If there's already a kubeconfig file in ~/.kube/config it will import that too and all the contexts
DEFAULT_KUBECONFIG_FILE="$HOME/.kube/config"
if test -f "${DEFAULT_KUBECONFIG_FILE}"
then
  export KUBECONFIG="$DEFAULT_KUBECONFIG_FILE"
fi

# Your additional kubeconfig files should be inside ~/.kube/config-files
ADD_KUBECONFIG_FILES="$HOME/.kube/config-files"
mkdir -p "${ADD_KUBECONFIG_FILES}"

OIFS="$IFS"
IFS=$'\n'
for kubeconfigFile in `find "${ADD_KUBECONFIG_FILES}" -type f -name "*.yml" -o -name "*.yaml"`
do
    export KUBECONFIG="$kubeconfigFile:$KUBECONFIG"
done
IFS="$OIFS"
```

⚠️ **Warning:** The above script conflicts with `kubectx`. If you want to use both, you should merge the configs:

```bash
kubectl config view --merge --flatten > $HOME/.kube/merged-config
export KUBECONFIG="$HOME/.kube/merged-config"
```

---

## ⚡ Commands

### 🌐 Networking

- **Connect Containers via Kubernetes DNS**  
    `<service-name>.<namespace>.svc.cluster.local`
    
- **Troubleshoot Networking**  
    Use the netshoot toolkit container:
    
    ```bash
    kubectl run tmp-shell --rm -i --tty --image nicolaka/netshoot -- /bin/bash
    ```
    

### 🛠️ Containers

- **Restart Deployments** (Stops and restarts all Pods):
    
    ```bash
    kubectl scale deploy <deployment> --replicas=0
    kubectl scale deploy <deployment> --replicas=1
    ```
    
- **Execute Commands on Pods**:
    
    ```bash
    kubectl exec -it <PODNAME> -- <COMMAND>
    kubectl exec -it generic-pod -- /bin/bash
    ```
    

### 🛠️ Config and Cluster Management

|Command|Description|
|---|---|
|`kubectl cluster-info`|Display endpoint information about the master and services.|
|`kubectl config view`|Get the configuration of the cluster.|

### 📦 Resource Management

|Command|Description|
|---|---|
|`kubectl get all --all-namespaces`|List all resources in the entire cluster.|
|`kubectl delete <RESOURCE> <RESOURCENAME> --grace-period=0 --force`|Force the deletion of the resource.|

---

## 🔢 Kubernetes Resource Short Names

|Short Name|Long Name|
|---|---|
|`csr`|`certificatesigningrequests`|
|`cs`|`componentstatuses`|
|`cm`|`configmaps`|
|`ds`|`daemonsets`|
|`deploy`|`deployments`|
|`ep`|`endpoints`|
|`ev`|`events`|
|`hpa`|`horizontalpodautoscalers`|
|`ing`|`ingresses`|
|`limits`|`limitranges`|
|`ns`|`namespaces`|
|`no`|`nodes`|
|`pvc`|`persistentvolumeclaims`|
|`pv`|`persistentvolumes`|
|`po`|`pods`|
|`pdb`|`poddisruptionbudgets`|
|`psp`|`podsecuritypolicies`|
|`rs`|`replicasets`|
|`rc`|`replicationcontrollers`|
|`quota`|`resourcequotas`|
|`sa`|`serviceaccounts`|
|`svc`|`services`|

---

## 🧰 Logs and Troubleshooting

### 🔍 Logs

- **Access MySQL Client Logs:**
    
    ```bash
    kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u USERNAME -h HOSTNAME -p
    ```
    
- **Troubleshoot Networking with Netshoot**:
    
    ```bash
    kubectl run -it --rm --image=nicolaka/netshoot netshoot -- /bin/bash
    ```
    

### 🚨 Resources Stuck in Terminating State

You can resolve stuck resources using the following method:

```bash
(
NAMESPACE=longhorn-demo-1
kubectl proxy &
kubectl get namespace $NAMESPACE -o json | jq '.spec = {"finalizers":[]}' > temp.json
curl -k -H "Content-Type: application/json" -X PUT --data-binary @temp.json 127.0.0.1:8001/api/v1/namespaces/$NAMESPACE/finalize
)
```

---

## Tags 📚

#kubectl #kubernetes #cli #cluster-management #resource-management