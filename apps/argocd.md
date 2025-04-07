# 🚀 Argo CD: GitOps Continuous Delivery for [[Kubernetes]]

**Argo CD** is a **declarative, GitOps** continuous delivery tool for [[Kubernetes]]. It enables automated deployment, lifecycle management, and version control of application definitions and configurations, making it a key tool for efficient Kubernetes application management.

**Documentation & Project Homepage**: [Argo CD Docs](https://argo-cd.readthedocs.io/en/stable/)

---

## 🔍 Overview

- **Product Type**: GitOps Continuous Delivery Tool
    
- **Focus**: Declarative application deployment and lifecycle management for [[Kubernetes]].
    
- **Key Uses**: GitOps-based deployment, [[Kubernetes]] app management, automated CI/CD workflows, and configuration version control.
    

---

## 🧠 Key Features of Argo CD

Argo CD offers a range of features designed to enhance the continuous delivery experience:

### 🛠️ GitOps-Based Deployment

> [!info]  
> **GitOps** allows you to declaratively manage the state of your Kubernetes applications by storing your configuration in Git repositories, making deployment automated and version-controlled.

- Declarative configuration management by connecting directly to Git repositories for configuration and deployment.
    

### 🌱 Multi-Cluster Support

> [!tip]  
> Manage multiple [[Kubernetes]] clusters with ease, allowing for deployment to any connected cluster, making Argo CD highly scalable for large infrastructure.

- Seamlessly manage multiple clusters, ensuring efficient deployment across various environments.
    

### 🔐 Secure and Scalable

> [!info]  
> Argo CD offers built-in security features such as Role-Based Access Control (RBAC), audit logs, and integration with identity providers to ensure secure deployment management.

- Role-based access control (RBAC), audit logs, and integration with popular identity providers for secure deployment management.
    

### 📦 Application Set Management

> [!warning]  
> Use the `ApplicationSet` resource to manage multiple applications with dynamic generation of application definitions. This enables efficient management of complex environments.

- Manage large sets of applications declaratively using `ApplicationSet`, enabling dynamic generation of application definitions.
    

### 🔄 Continuous Sync

> [!info]  
> Argo CD can automatically sync applications with the state defined in the Git repository, ensuring the deployed application is always up-to-date with the latest changes.

- Automatically sync applications with the state defined in the Git repository, ensuring the deployed application is always up-to-date.
    

---

## 🚨 Installation

### 1. **Install Argo CD on a [[Kubernetes]] Cluster using [[kubectl]]**

```bash
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 2. **Add [[Traefik]] IngressRoute**

> [!tip]  
> IngressRoute allows Argo CD to be exposed via Traefik, making it accessible for external traffic.

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: argocd-server
  namespace: argocd
spec:
  entryPoints:
    - websecure
  routes:
    - kind: Rule
      match: Host(`argocd.example.com`)
      priority: 10
      services:
        - name: argocd-server
          port: 80
    - kind: Rule
      match: Host(`argocd.example.com`) && Headers(`Content-Type`, `application/grpc`)
      priority: 11
      services:
        - name: argocd-server
          port: 80
          scheme: h2c
  tls:
    certResolver: default
```

### 3. **Disable Internal TLS**

> [!warning]  
> Disabling internal TLS allows easier external access, but ensure proper security measures are in place to protect sensitive data.

Edit the `--insecure` flag in the `argocd-server` command or set `server.insecure: "true"` in the `argocd-cmd-params-cm` ConfigMap.

---

## 🔑 Get the Admin Password

> [!info]  
> The admin password for Argo CD is initially set to the name of the server pod in versions prior to v1.9. For v1.9 and later, you can retrieve the password using the following command.

For Argo CD v1.8 and earlier, the initial password is set to the name of the server pod. For Argo CD v1.9 and later, use the following command to retrieve the initial password:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

---

## ⚙️ Configuration

### Add Private GitHub Repositories

1. **Create a GitHub Token**: [GitHub Tokens](https://github.com/settings/tokens)
    
2. **Add New Repository in ArgoCD via kubectl or the GUI**
    

> [!tip]  
> Store the GitHub repository credentials securely using Kubernetes secrets for Argo CD to access private repositories.

```yaml
apiVersion: v1  
kind: Secret  
metadata:  
  name: repo-private-1
  labels:  
    argocd.argoproj.io/secret-type: repository  
stringData:  
  url: https://github.com/xcad2k/private-repo 
  password: <github-token> 
  username: not-used
```

3. **Verify Repository Connection**: Ensure that the new repository is correctly connected.
    

---

### Declarative Application and ApplicationSet

> [!info]  
> `ApplicationSet` allows managing applications declaratively across multiple clusters, simplifying the workflow for larger teams and more complex environments.

**Application Example:**

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: guestbook
  namespace: argocd
spec:
  destination:
    namespace: default
    server: 'https://kubernetes.default.svc'
  source:
    path: kustomize-guestbook
    repoURL: 'https://github.com/argoproj/argocd-example-apps'
    targetRevision: HEAD
  project: default
  syncPolicy:
    automated:
      prune: false
      selfHeal: false
```

**ApplicationSet Example:**

```yaml
apiVersion: argoproj.io/v1alpha1
kind: ApplicationSet
metadata:
  name: guestbook
  namespace: argocd
spec:
  generators:
  - clusters: {} # Cluster generator
  template: 
    metadata:
      name: '{{name}}-guestbook'
    spec:
      project: "default"
      source:
        repoURL: https://github.com/argoproj/argocd-example-apps/
        targetRevision: HEAD
        path: kustomize-guestbook
      destination:
        server: '{{server}}'
        namespace: default
```

---

## 🌍 Explore More

- **[Argo CD Quickstart](https://argo-cd.readthedocs.io/en/stable/getting_started/)** — Get started with Argo CD in minutes with this quick guide.
    
- **[CI/CD with Kubernetes](https://www.example.com/cicd-kubernetes)** — Learn more about building [[CI/CD]] pipelines with [[Kubernetes]] and [[GitOps]].
    

---

## 🏷️ Tags

#argocd  
#gitops  
#kubernetes  
#continuous-delivery  
#automation  
#cicd  
#traefik  
#cloud-native