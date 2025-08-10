## Installation

Pull the docker image and mount a volume from the host for persistent storage:

```sh
docker pull vaultwarden/server:latest
docker run -d --name vaultwarden -v /vw-data/:/data/ -p 80:80 vaultwarden/server:latest
```

This will preserve any persistent data under /vw-data/, you can adapt the path to whatever suits you.

**IMPORTANT**: Some web browsers, like Chrome, disallow the use of Web Crypto APIs in insecure contexts. In this case, you might get an error like `Cannot read property 'importKey'`. To solve this problem, you need to access the web vault from HTTPS.

This can be configured in [vaultwarden directly](https://github.com/dani-garcia/vaultwarden/wiki/Enabling-HTTPS) or using a third-party reverse proxy ([some examples](https://github.com/dani-garcia/vaultwarden/wiki/Proxy-examples)).

If you have an available domain name, you can get HTTPS certificates with [Let's Encrypt](https://letsencrypt.org/), or you can generate self-signed certificates with utilities like [mkcert](https://github.com/FiloSottile/mkcert). Some proxies automatically do this step, like Caddy (see examples linked above).

## Usage

See the [vaultwarden wiki](https://github.com/dani-garcia/vaultwarden/wiki) for more information on how to configure and run the vaultwarden server.