# 🚀 Traefik

> [!info]  
> **Traefik** is an open-source Edge [[Router]] designed for easy and dynamic routing of traffic to [[Docker]], [[Kubernetes]], and other services. It automatically discovers services and configures itself, enabling you to publish applications effortlessly and securely.

🌐 **Project Homepage**: [Traefik](https://www.traefik.io/)  
📜 **Documentation**: [Traefik Docs](https://doc.traefik.io/traefik/)

---

## 🔍 Overview

> [!info]  
> **Traefik** simplifies routing for modern cloud-native applications by integrating with [[Docker]], [[Kubernetes]], and more. It automatically handles traffic distribution, security, and scaling without complex configurations.

### Why Use Traefik?

- **Dynamic Service Discovery**: Automatically configures routes to services.
    
- **Integrated #SSL**: Traefik supports automatic #SSL certificates via #ACME and integrates easily with [[Let's Encrypt]].
    
- ** #Multi-cluster and #Multi-cloud**: Seamlessly deploys across various platforms like [[Docker]], [[Kubernetes]], and [[Swarm]].
    
- **Rich Dashboard**: Provides a comprehensive UI to manage and monitor your routes and services.
    

---

## 🛠️ Features

> [!tip]  
> Traefik enhances your workflow with several powerful features:

- 🌐 #Multi-Provider **Support**: Supports [[Docker]], [[Kubernetes]], [[Swarm]], and more.
    
- 🔒 #HTTPS **and** #TLS: Automatic #SSL certificate generation with [[Let's Encrypt]] or custom certs.
    
- 🔄 **Auto-scaling**: Automatically routes traffic based on the available services and replicas.
    
- 📊 **Dashboard**: Real-time visibility of traffic, service status, and more.
    
- ⚙️ **Easy Configuration**: Configuration via simple #YAML files or via providers ([[Docker]], [[Kubernetes]], etc.).
    

---

## 🏃 Getting Started

### 🧑‍💻 Install Traefik

> [!info]  
> To install Traefik on [[Kubernetes]] using [[Helm]], follow these commands:

```sh
helm repo add traefik https://traefik.github.io/charts
helm repo update
helm install traefik traefik/traefik
```

> [!warning]  
> The Docker installation method is still a work in progress (WIP). Please refer to the [official documentation](https://doc.traefik.io/traefik/) for the latest updates.

---

## 🔧 Configuration

### 🌐 EntryPoints

#### #HTTP Redirection

You can define #HTTP redirection to #HTTPS with the following configuration:

```yaml
entryPoints:
  web:
    address: :80
    http:
      redirections:
        entryPoint:
          to: websecure
          scheme: https
```

#### #HTTPS Configuration

To enable #HTTPS:

```yaml
entryPoints:
  websecure:
    address: :443
```

---

### 🛠️ Routers

#### **traefik.http.routers.router.entrypoints**

Specifies which entrypoints the router listens on. Setting this to `traefik.http.routers.router.entrypoints: websecure` will expose the container on the `websecure` entrypoint.

> [!tip]  
> When using `websecure`, enable `traefik.http.routers.router.tls` to activate #TLS.

#### **traefik.http.routers.router.rule**

Defines the rules for the router, such as #FQDN, PathPrefix, etc.

```yaml
- "traefik.enable=true"
- "traefik.http.routers.nginx-test.entrypoints=websecure"
- "traefik.http.routers.nginx-test.tls=true"
- "traefik.http.routers.nginx-test.rule=PathPrefix(`/nginx-test/`)"
- "traefik.http.routers.nginx-test.middlewares=nginx-test"
- "traefik.http.middlewares.nginx-test.stripprefix.prefixes=/nginx-test"
```

---

### 🔐 CertificatesResolvers

To enable DNS-based challenges (e.g., using Cloudflare, DigitalOcean, etc.) for #ACME certificates:

```yaml
certificatesResolvers:
  yourresolver:
    acme:
      email: "your-mail-address"
      dnsChallenge:
        provider: your-dns-provider
        resolvers:
          - "your-dns-resolver-ip-addr:53"
```

---

### 🔒 ServersTransport

#### InsecureSkipVerify

To skip #TLS verification from **Traefik** to your **Servers**, you can configure it like this:

```yaml
serversTransport:
  insecureSkipVerify: true
```

---

### 🛡️ TLS Settings

#### defaultCertificates

Define default certificates in Traefik:

```yaml
tls:
  stores:
    default:
      defaultCertificate:
        certFile: /your-traefik-cert.crt
        keyFile: /your-traefik-key.key
```

#### options

Define #TLS options like disabling insecure #TLS versions:

```yaml
tls:
  options:
    default:
      minVersion: VersionTLS12
```

---

## 🔄 Related

- **[[Docker]]** — Container platform supported by Traefik for easy integration.
    
- **[[Kubernetes]]** — Orchestrator supported by Traefik for managing containerized applications.
    
- **[[Helm]]** — Package manager for Kubernetes used to install Traefik.
    

---

## 🌍 Explore More

- 🌐 [Traefik Documentation](https://doc.traefik.io/traefik/)
    
- 🌐 [Traefik GitHub Repository](https://github.com/traefik/traefik)
    

---

## 📚 Tags

- #Traefik
    
- #Docker
    
- #Kubernetes
    
- #HTTPS
    
- #TLS
    
- #Routing
    
- #DevOps
    
- #Cloud
    