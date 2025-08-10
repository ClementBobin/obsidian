[github](https://github.com/louislam/uptime-kuma)
## ⭐ Features

- Monitoring uptime for HTTP(s) / TCP / HTTP(s) Keyword / HTTP(s) Json Query / Ping / DNS Record / Push / Steam Game Server / Docker Containers
- Fancy, Reactive, Fast UI/UX
- Notifications via Telegram, Discord, Gotify, Slack, Pushover, Email (SMTP), and [90+ notification services, click here for the full list](https://github.com/louislam/uptime-kuma/tree/master/src/components/notifications)
- 20-second intervals
- [Multi Languages](https://github.com/louislam/uptime-kuma/tree/master/src/lang)
- Multiple status pages
- Map status pages to specific domains
- Ping chart
- Certificate info
- Proxy support
- 2FA support
## 🔧 How to Install

### 🐳 Docker

```shell
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1
```
#### Docker-compose:
```yml
# Simple docker-compose.yml
# You can change your port or volume location

version: '3.3'

services:
  uptime-kuma:
    image: louislam/uptime-kuma:1
    container_name: uptime-kuma
    volumes:
      - ./uptime-kuma-data:/app/data
    ports:
      - 3001:3001  # <Host Port>:<Container Port>
    restart: always
```

Uptime Kuma is now running on [http://localhost:3001](http://localhost:3001)

>Warning
>
>File Systems like **NFS** (Network File System) are **NOT** supported. Please map to a local directory or volume.

### Advanced Installation

If you need more options or need to browse via a reverse proxy, please read:

[https://github.com/louislam/uptime-kuma/wiki/%F0%9F%94%A7-How-to-Install](https://github.com/louislam/uptime-kuma/wiki/%F0%9F%94%A7-How-to-Install)

# Reverse Proxy
https://github.com/louislam/uptime-kuma/wiki/Reverse-Proxy

## Reverse Proxy with cloudflare
https://github.com/louislam/uptime-kuma/wiki/Reverse-Proxy-with-Cloudflare-Tunnel

## Nginx

With SSL:

```nginx
server {
  listen 443 ssl http2;
  # Remove '#' in the next line to enable IPv6
  # listen [::]:443 ssl http2;
  server_name sub.domain.com;
  ssl_certificate     /path/to/ssl/cert/crt;
  ssl_certificate_key /path/to/ssl/key/key;
  # *See "With SSL (Certbot)" below for details on automating ssl certificates

  location / {
    proxy_set_header   X-Real-IP $remote_addr;
    proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header   Host $host;
    proxy_pass         http://localhost:3001/;
    proxy_http_version 1.1;
    proxy_set_header   Upgrade $http_upgrade;
    proxy_set_header   Connection "upgrade";
  }
}
```

Without SSL:

```nginx
server  {
    listen 80;
    # Remove '#' in the next line to enable IPv6
    # listen [::]:80;
    server_name    sub.domain.com;
    location / {
        proxy_pass         http://localhost:3001;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection "upgrade";
        proxy_set_header   Host $host;
    }
}
```

With SSL (Certbot):

```nginx
server {
  # If you don't have one yet, you can set up a subdomain with your domain registrar (e.g. Namecheap)
  # Just create a new host record with type='A Record', host='<subdomain>', value='<ip_address>'.
  
  server_name your_subdomain.your_domain.your_tld;

  location / {
    proxy_set_header   X-Real-IP $remote_addr;
    proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header   Host $host;
    proxy_pass         http://localhost:3001/;
    proxy_http_version 1.1;
    proxy_set_header   Upgrade $http_upgrade;
    proxy_set_header   Connection "upgrade";
  }
}

# Once that's completed, you can run
# sudo apt install python3-certbot-nginx
# sudo certbot --nginx -d your_domain -d your_subdomain.your_domain -d www.your_domain
# And Certbot will auto-populate this nginx .conf file for you, while also renewing your certificates automatically in the future.
```

# 🆙 How to Update

##### Clone this wiki locally

## 🆙🐳 Docker

Re-pull the latest docker image and create another container with the same volume.

For someone who used my "How-to-use" commands to install Uptime Kuma, you can update by this:

```shell
docker pull louislam/uptime-kuma:1
docker stop uptime-kuma
docker rm uptime-kuma

# Default
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1

# If you are not using default value
# docker run -d --restart=always -p <YOUR PORT>:3001 -v <YOUR VOLUME>:/app/data --name uptime-kuma louislam/uptime-kuma:1
```

PS: For every new release, it takes some time to build the docker image, please be patient if it is not available yet.

## Docker-Compose

```shell
cd "<YOUR docker-compose.yml DIRECTORY>"
docker compose pull
docker compose up -d --force-recreate
```

## 🆕 What's Next?

I will assign requests/issues to the next milestone.

[https://github.com/louislam/uptime-kuma/milestones](https://github.com/louislam/uptime-kuma/milestones)

# Monitor Docker
## If you are running Uptime Kuma Docker

By default, a docker container is self-contained, which means Uptime Kuma cannot access your host. You need to bind the /var/run/docker.sock to your container.

### (Method 1) Share docker.sock with Uptime Kuma Container

Command argument:

```shell
-v /var/run/docker.sock:/var/run/docker.sock
```

docker-compose:

```yaml
volumes:
   - /var/run/docker.sock:/var/run/docker.sock
```

### (Method 2) TCP - Bridge Mode

**Expose TCP port**  
To enable TCP monitoring, you need to first expose the Docker daemon on a TCP port. The primary documentation is available [here](https://docs.docker.com/config/daemon/) but the example below provides some quick options.

Update the daemon configuration located at `/etc/docker/daemon.json`:

```json
{
   #any additional parameters should be kept

   #Insecure option, only use this if you are running on a closed network
   "hosts": ["unix:///var/run/docker.sock", "tcp://<host IP address>:2375"]

   #Secure option
   "tls": true,
   "tlscert": "/var/docker/server.pem",
   "tlskey": "/var/docker/serverkey.pem",
   "hosts": ["unix:///var/run/docker.sock", "tcp://<host IP address>:2376"]
}
```

Restart the daemon using `sudo systemctl restart docker.service`.

If the daemon fails to start, it may be because there are duplicate keys, in this case hosts, -H, that is already part of the daemon configuration.

You can edit the startup configuration using `sudo systemctl edit docker.service`.

```toml
[Service]
#The blank ExecStart is required to clear the current entry point
ExecStart=
#Replace the existing ExecStart but only remove the properties that you have added into the daemon.json file, leave all else the same.
ExecStart=/usr/bin/dockerd --containerd=/run/containerd/containerd.sock
```

My original ExecStart was: `ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock`, note the -H that would cause a duplicate property error.

Note

If you installed docker using snap

Snap stores the `daemon.json` here: `/var/snap/docker/current/config/daemon.json`

use `sudo nano /var/snap/docker/current/config/daemon.json` to edit the file like

```diff
{
    "log-level":        "error",
    "storage-driver":   "overlay2",
+   "hosts": ["unix:///var/run/docker.sock", "tcp://0.0.0.0:2375"]
}
```

- Restart the service using `sudo systemctl restart snap.docker.dockerd.service`
- Check if the service is running using `sudo systemctl status snap.docker.dockerd.service`

The service should be running as usual, showing the docker snap service

![Screenshot showing the snap docker service working](https://private-user-images.githubusercontent.com/642149/265128175-8494c876-5580-4f87-9ceb-9a5974f1c977.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDUzMTU0NDUsIm5iZiI6MTcwNTMxNTE0NSwicGF0aCI6Ii82NDIxNDkvMjY1MTI4MTc1LTg0OTRjODc2LTU1ODAtNGY4Ny05Y2ViLTlhNTk3NGYxYzk3Ny5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTE1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExNVQxMDM5MDVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00ZDU0NmRiOGY0ZGJiMTg1NGI4NjUzYTI3NzA2NDdmYTY4ZjVlMjY4YjNiZWY3YjJjMjA2N2UwNjU5NWNmMTE2JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.BQbBns99yE11l6_8S538-fGmfi3a9OhtnoxT0_N-CUM)

**Update uptime-kuma**  
Add a new Docker host and choose TCP as the option. Specify the IP address of the host and the TCP port you exposed, as seen below.

![Docker host monitor](https://github.com/louislam/uptime-kuma/wiki/img/docker-host.png)

**Configuring certificates for Docker TLS connection**

Assuming you have already properly configured your remote docker instance to listen securely for TLS connections as detailed [here](https://docs.docker.com/engine/security/protect-access/#use-tls-https-to-protect-the-docker-daemon-socket), you must configure Uptime-Kuma to use the certificates you've generated. The base path where certificates are looked for can be set with the `DOCKER_TLS_DIR_PATH` environmental variable or defaults to `data/docker-tls/`.

If a directory in this path exists with a name matching the FQDN of the docker host (e.g. the FQDN of `https://example.com:2376` is `example.com` so the directory `data/docker-tls/example.com/` would be searched for certificate files), then `ca.pem`, `key.pem` and `cert.pem` files are loaded and included in the agent options. File names can also be overridden via `DOCKER_TLS_FILE_NAME_(CA|KEY|CERT)`.

# Add-on
https://github.com/louislam/uptime-kuma/wiki/3rd-Party-Addons-Apps
