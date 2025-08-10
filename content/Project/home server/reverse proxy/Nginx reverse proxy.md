![](https://nginxproxymanager.com/github.png)  
  
![](https://img.shields.io/badge/version-2.10.4-green.svg?style=for-the-badge)
# Install
This project comes as a pre-built docker image that enables you to easily forward to your websites running at home or otherwise, including free SSL, without having to know too much about Nginx or Letsencrypt.

- [Quick Setup](https://nginxproxymanager.com/guide/#quick-setup)
- [Full Setup](https://nginxproxymanager.com/setup/)

## Project Goal

I created this project to fill a personal need to provide users with a easy way to accomplish reverse proxying hosts with SSL termination and it had to be so easy that a monkey could do it. This goal hasn't changed. While there might be advanced options they are optional and the project should be as simple as possible so that the barrier for entry here is low.
## Features

- Beautiful and Secure Admin Interface based on [Tabler](https://tabler.github.io/)


- Easily create forwarding domains, redirections, streams and 404 hosts without knowing anything about Nginx
- Free SSL using Let's Encrypt or provide your own custom SSL certificates
- Access Lists and basic HTTP Authentication for your hosts
- Advanced Nginx configuration available for super users
- User management, permissions and audit log

## Hosting your home network

I won't go in to too much detail here but here are the basics for someone new to this self-hosted world.

1. Your home router will have a Port Forwarding section somewhere. Log in and find it
2. Add port forwarding for port 80 and 443 to the server hosting this project
3. Configure your domain name details to point to your home, either with a static ip or a service like DuckDNS or [Amazon Route53](https://github.com/jc21/route53-ddns)


1. Use the Nginx Proxy Manager as your gateway to forward to your other web based services

## Quick Setup

1. Install Docker and Docker-Compose

- [Docker Install documentation](https://docs.docker.com/install/)

[Docker-Compose Install documentation](https://docs.docker.com/compose/install/)

2. Create a docker-compose.yml file similar to this:

```
version: '3.8'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

This is the bare minimum configuration required. See the [documentation](https://nginxproxymanager.com/setup/)


for more.

3. Bring up your stack by running

```
docker-compose up -d

# If using docker-compose-plugin
docker compose up -d

```

4. Log in to the Admin UI

When your docker container is running, connect to it on port `81` for the admin interface. Sometimes this can take a little bit because of the entropy of keys.

[http://127.0.0.1:81](http://127.0.0.1:81)


Default Admin User:

```
Email:    admin@example.com
Password: changeme
```

Immediately after logging in with this default user you will be asked to modify your details and change your password.

## Contributors

Special thanks to [all of our contributors](https://github.com/NginxProxyManager/nginx-proxy-manager/graphs/contributors)

.

## Getting Support

1. [Found a bug?](https://github.com/NginxProxyManager/nginx-proxy-manager/issues)

[Reddit](https://reddit.com/r/nginxproxymanager)
# Running
[run doc](https://nginxproxymanager.com/setup/#running-the-app)
# Advance config
[advance doc](https://nginxproxymanager.com/advanced-config/)
# Upgrading

```
docker-compose pull
docker-compose up -d
```

This project will automatically update any databases or other requirements so you don't have to follow any crazy instructions. These steps above will pull the latest updates and recreate the docker containers.

See the [list of releases](https://github.com/NginxProxyManager/nginx-proxy-manager/releases)

for any upgrade steps specific to each release.

# Third Party

As this software gains popularity it's common to see it integrated with other platforms. Please be aware that unless specifically mentioned in the documentation of those integrations, they are _not supported_ by me.

Known integrations:

- [HomeAssistant Hass.io plugin](https://github.com/hassio-addons/addon-nginx-proxy-manager)
- [UnRaid / Synology](https://github.com/jlesage/docker-nginx-proxy-manager)
- [Proxmox Scripts](https://github.com/ej52/proxmox-scripts/tree/main/apps/nginx-proxy-manager) 
- [nginxproxymanagerGraf](https://github.com/ma-karai/nginxproxymanagerGraf)