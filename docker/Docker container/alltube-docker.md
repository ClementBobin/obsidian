# 🎬 AllTube Quick Start

[AllTube](https://github.com/Rudloff/alltube) is a Web GUI for [youtube-dl](https://github.com/ytdl-org/youtube-dl), which allows you to download videos from various websites—even those that don't explicitly allow video downloads.

AllTube provides an [official site](http://alltubedownload.net/) for using _youtube-dl_ online or you can deploy your own instance under your domain.

> [!note] The deployment of AllTube can be a bit cumbersome, but using Docker simplifies the process significantly. Let's walk through setting it up!

---

## ⚙️ Prerequisites

Before getting started, ensure you have a **Docker environment**. If you don’t, follow the official Docker installation guide [here](https://docs.docker.com/engine/install/).

---

## 🚀 Quick Start with Docker

To deploy AllTube using Docker, run the following command:

```shell
docker run -d --restart always --name alltube -p 24488:80 dnomd343/alltube
```

This command will start AllTube on port `24488`. You can change this port to your preferred one.

> [!tip] You can customize AllTube’s behavior by passing environment variables. Below are a few built-in options you can use:

### Available Environment Variables

- `TITLE=...` : Set the title of your website.
    
- `REMUX=ON` : Merge best audio and video.
    
- `STREAM=ON` : Allow video streaming.
    
- `CONVERT=ON` : Enable audio conversion.
    
- `PORT=...` : Specify a custom port (default: `80`).
    

---

### Example Command with Custom Configuration

```shell
docker run -d --restart always --name alltube \
  --env TITLE="My AllTube Site" \
  --env CONVERT=ON \
  --env STREAM=ON \
  --env REMUX=ON \
  --env PORT=24488 \
  --network host dnomd343/alltube
```

---

## 🖥️ Configure Reverse Proxy (e.g., Nginx)

To access AllTube through your domain, configure a reverse proxy with Nginx:

```nginx
server {
    listen 80;
    server_name video.343.re;  # your domain
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name video.343.re;  # your domain
    ssl_certificate /etc/ssl/certs/343.re/fullchain.pem;  # TLS certificate of your domain
    ssl_certificate_key /etc/ssl/certs/343.re/privkey.pem;  # TLS private key of your domain
    location / {
        proxy_http_version 1.1;
        proxy_set_header Connection '';
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_pass http://127.0.0.1:24488;
    }
}
```

> [!warning] After making these changes, don't forget to reload Nginx with the command: `nginx -s reload`

Now, you can visit your domain and enjoy AllTube!

---

## 🔧 Advanced Setup

If you'd like to build the AllTube Docker image yourself, use the following command:

```shell
docker build -t alltube https://github.com/dnomd343/alltube-docker.git
```

> [!note] By default, AllTube uses the **yt-dlp** project (a more updated fork of youtube-dl) instead of youtube-dl. You can manually change `YTDLP` in the Dockerfile to specify the version you want.

---

## 🧰 Customization

If you don’t need the audio conversion feature, you can exclude `ffmpeg` during the build process to reduce the image size.

### Build Multi-Architecture Images

To speed up the build process, use Docker's multi-stage builds. Here’s an example using `buildx` to build images for multiple architectures:

```shell
docker buildx build -t dnomd343/alltube \
  --platform="linux/amd64,linux/386,linux/arm64,linux/arm/v7" \
  https://github.com/dnomd343/alltube-docker.git --push
```

This will create and push images for multiple platforms.

---

## 📝 Conclusion

AllTube makes it easy to deploy a video download site based on youtube-dl. With Docker and some basic configurations, you can quickly get started and enjoy the flexibility to customize and scale your deployment.

---

## Tags 📚

#alltube #docker #yt-dlp #videos #web