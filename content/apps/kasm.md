# 🐳 KASM Workspaces Guide

> [!abstract]  
> **Streaming containerized apps and desktops to end-users.**  
> The Workspaces platform provides enterprise-class orchestration, data loss prevention, and web streaming technology to enable the delivery of containerized workloads directly to your browser.

---

## 🔍 Overview

- **Product Type**: Containerized Application Platform
    
- **Focus**: Deliver secure, containerized desktop environments via web browser.
    
- **Use Cases**:
    
    - Secure remote workspaces
        
    - Web-isolated browsing
        
    - Application sandboxing
        

---

## 🛠️ Features

- **Web-Streamed Workspaces**: Access apps and desktops directly in the browser.
    
- **Security**: Built-in DLP and user session isolation.
    
- **Container Orchestration**: Customize and control container behavior.
    
- **Docker Support**: Import custom container images and registries.
    
- **SSL Management**: Easily integrate self-signed or trusted certificates.
    

---

## 🏃 Getting Started

> [!tip]  
> Ensure Docker is installed and running before starting Kasm Workspaces setup.

### 🔒 Add Self-Signed SSL Certificates

#### 🛑 1. Stop the Kasm services

```bash
sudo /opt/kasm/bin/stop
```

#### 📁 2. Replace certificate files

```bash
sudo cp <your_cert> /opt/kasm/current/certs/kasm_nginx.crt
sudo cp <your_key> /opt/kasm/current/certs/kasm_nginx.key
```

#### ▶️ 3. Start the Kasm services

```bash
sudo /opt/kasm/bin/start
```

---

## 🔧 Customization and Configuration

### 🧱 Custom Images

#### 🌐 Docker Registry URL

```bash
https://index.docker.io/v1/
```

> [!warning] Tag Required  
> You **must** include a `tag` in your Docker image.  
> Kasm will not pull or launch the image properly without it.

#### 🐋 Docker Run Config (Example)

```json
{
  "cap_add": ["NET_ADMIN"],
  "devices": ["dev/net/tun", "/dev/net/tun"],
  "sysctls": {
    "net.ipv6.conf.all.disable_ipv6": "0"
  }
}
```

---

## 🛠️ Troubleshooting

### 💠 Kasm Agent

> [!todo]  
> Add Kasm Agent troubleshooting steps here.

### 🗄️ Database Access

```bash
sudo docker exec -it kasm_db psql -U kasmapp -d kasm
```

---

## 🧹 Clean Up Invalid Users from `user_groups`

### 1️⃣ Check the table for invalid entries

```sql
select * from user_groups;
```

> [!example] Output

```
 user_group_id                          | user_id                               | group_id
----------------------------------------+----------------------------------------+----------------------------------------
 07c54672-739f-42d8-befc-bb2ba29fa22d   | 71899524-5b31-41ac-a359-1aa8a008b831   | 68d557ac-4cac-42cc-a9f3-1c7c853de0f3
 e291f1f7-86be-490f-9f9b-3a520d4d1dfa   | 71899524-5b31-41ac-a359-1aa8a008b831   | b578d8e9-5585-430b-a70b-9935e8acaaa3
 07b6f450-2bf5-48c0-9c5e-3443ad962fcb   |                                        | 68d557ac-4cac-42cc-a9f3-1c7c853de0f3
 8c4c7242-b2b5-4a7a-89d3-e46d24456e5c   |                                        | b578d8e9-5585-430b-a70b-9935e8acaaa3
```

### 2️⃣ Delete invalid rows (where `user_id` is NULL)

```sql
delete from user_groups where user_id is null;
```

### 3️⃣ Verify the cleanup

```sql
select * from user_groups;
```

> [!success] Clean Output

```
 user_group_id                          | user_id                               | group_id
----------------------------------------+----------------------------------------+----------------------------------------
 07c54672-739f-42d8-befc-bb2ba29fa22d   | 71899524-5b31-41ac-a359-1aa8a008b831   | 68d557ac-4cac-42cc-a9f3-1c7c853de0f3
 e291f1f7-86be-490f-9f9b-3a520d4d1dfa   | 71899524-5b31-41ac-a359-1aa8a008b831   | b578d8e9-5585-430b-a70b-9935e8acaaa3
```

---

## 🔄 Related

- **[[Docker]]** — Foundation for container image management and runtime.
    
- **[[PostgreSQL]]** — Default database backend for Kasm.
    
- **[[nginx]]** — Used as a reverse proxy within Kasm for SSL termination.
    

---

## 🌍 Explore More

- 🌍 [Kasm Official Docs](https://www.kasmweb.com/docs/)
    
- 🌍 [Kasm GitHub](https://github.com/kasmtech/workspaces)
    
- 🌍 [Kasm Support Portal](https://www.kasmweb.com/contact)
    

---

## 📚 Tags

- #Kasm
    
- #Docker
    
- #SSL
    
- #Workspaces
    
- #Containerization
    
- #Security
    
- #PostgreSQL
    
- #WebStreaming
    
- #Linux
    
