# 🧭 Nginx

> [!info] **Nginx** is a high-performance open-source web server, reverse proxy, and application server.  
> It's widely used for serving static content, load balancing, SSL termination, and acting as a gateway to application services.

🌐 **Project Homepage**: [Nginx Homepage](https://www.nginx.com/)  
📚 **Documentation**: [Nginx Unit Docs](https://unit.nginx.org/)

---

## 🔍 Overview

- **Type**: Web Server / Reverse Proxy / Application Gateway
    
- **Purpose**: Serve static content, reverse proxy dynamic apps, terminate SSL, balance load
    
- **Key Capabilities**:
    
    - HTTP/2 and experimental HTTP/3 support
        
    - Custom logging, access control
        
    - Powerful location-based routing
        
    - SSL certificate management
        

---

## 🛠️ Features

- 🌐 HTTP/HTTPS server with static file hosting
    
- 🔀 Reverse proxy and load balancing
    
- 📜 Flexible configuration using `nginx.conf`
    
- 🔒 SSL termination and security headers
    
- 🧩 Modular architecture for custom extensions
    
- 🛠️ FastCGI, SCGI, uWSGI, and gRPC support
    

---

## 🏃 Getting Started

### 🧾 Basic Configuration

```nginx
error_log logs/error.log;
error_log logs/debug.log debug;
```

```nginx
listen 80;
listen 443 ssl http2;
listen 443 http3 reuseport; # experimental
```

```nginx
server_name domain1.com *.domain1.com;

root /var/www/html/domain1;
index index.php;
```

> [!tip] SSL Config  
> Nginx supports SSL out of the box — make sure to provide valid certificate and key files.

```nginx
ssl_certificate cert.pem;
ssl_certificate_key cert.key;
```

---

## 🔧 Customization and Configuration

### 🧠 Header Manipulation

```nginx
add_header Alt-svc '$http3=":443"; ma=86400'; # experimental
```

### 📂 Location Blocks

```nginx
location / {
    root /var/www/html;
    index index.html index.htm;
}
```

```nginx
location / {
    try_files $uri $uri/ /index.php$is_args$args;
}
```

```nginx
location ~ \.php$ {
    fastcgi_pass 127.0.0.1:9000;
    fastcgi_index index.php;
    fastcgi_param SCRIPT_FILENAME /scripts$fastcgi_script_name;
    include fastcgi_params;
}
```

> [!warning] Always secure sensitive paths like `.ht` or backup files.

```nginx
location ~ /\.ht {
    deny all;
}
```

---

## 🔁 Reverse Proxy

### 🔍 Show Client’s Real IP

```nginx
server {
    server_name example.com;

    location / {
        proxy_pass http://localhost:4000;

        # Preserve client IP info
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

> [!tip]  
> Use `proxy_set_header` for proper header forwarding when using Nginx as a reverse proxy behind load balancers or CDNs.

---

## 🔄 Related

- **[[Let's Encrypt]]** — Free SSL certificate provider
    
- **[[Docker]]** — Frequently used with Nginx for containerized deployments
    
- **[Nginx Config Examples](https://www.digitalocean.com/community/tools/nginx)** — Handy tool to generate configs
    

---

## 🌍 Explore More

- 🌐 [Nginx Beginner’s Guide](https://nginx.org/en/docs/beginners_guide.html)
    
- 🌐 [Nginx Configuration Guide](https://nginx.org/en/docs/)
    
- 🌐 [Nginx GitHub](https://github.com/nginx/nginx)
    

---

## 📚 Tags

- #Nginx
    
- #WebServer
    
- #ReverseProxy
    
- #LoadBalancing
    
- #SSL
    
- #HTTP3
    
- #FastCGI
    
- #DevOps
    