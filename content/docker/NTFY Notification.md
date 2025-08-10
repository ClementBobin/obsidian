# NTFY Notifications  
NTFY is a notification tool that allows users to send notifications from the command line. It is a versatile tool that supports various notification services.  
## Overview  NTFY 
notifications can be visualized through the following concept map:

```
.----------------. 
|  NTFY command  |----------. 
'----------------'          | 
							| 
						passed to 
							| 
							| 
+------|--------------------|--------------------------------+ 
| NTFY |                    V                                |
|      | +-------------------------+                         | 
|      | |  notification  service  |-----.                   | 
|      | +-------------------------+     |                   | 
|      |              |                  |                   | 
|      |           manages               |                   | 
|      |              |                  |                   | 
|      |              V                  |                   | 
|      |  +----------------------+       |                   |  
|      '->| notification message |       |                   | 
|         +----------------------+       |                   |   
|                     |                  |                   | 
|                   sends                |                   | 
|                     |                  V                   | 
|                     V       +---------------------+        | 
|                 delivers    | notification channel|        | 
|                             +---------------------+        | 
|                                                            | 
|                  +--------------+                          | 
|                  | notification |                          |
|                  |  receiver    |                          | 
|                  +--------------+                          | 
+------------------------------------------------------------+
```

At the core is the `ntfy` command, which users utilize to trigger notifications through various notification services.  
The `notification service` is responsible for sending notification messages to specific channels or receivers based on the user's request.  
Each notification message is composed of a `notification message` and is delivered to a `notification receiver`.  
## Notification Message Structure  
A typical notification message consists of the following elements:  
- Title: A concise title or subject for the notification. 
- Body: The main content or message of the notification. 
- Icon: An optional icon or image associated with the notification. 
- Actions: Optional actions that can be taken directly from the notification.  Here is an example of a notification message structure:

```
Title: New Email Body: You have received a new email from John Doe. Icon: email_icon.png Actions: [Open, Archive, Reply]
```

This structure allows for clear and informative notifications.  
## Usage  
To send a notification using NTFY, the user typically executes the `ntfy` command with appropriate options and arguments to specify the notification service, title, body, and other optional components.  
For example:  
```bash 
ntfy -t "New Email" -b "You have received a new email from John Doe." -i email_icon.png -a "Open,Archive,Reply"
```


This command triggers a notification with the specified details.

> **Note**: The exact syntax and options may vary based on the chosen notification service.

## Supported Notification Services

NTFY supports a variety of notification services, including but not limited to:

- Email
- Pushbullet
- Slack
- Telegram
- Twilio
- and more.

Users can choose the appropriate service based on their preferences and requirements.

For more information on how to use NTFY and the available options, please refer to the [NTFY documentation](https://ntfy.readthedocs.io/).

# Install

The `ntfy` CLI allows you to [publish messages](https://docs.ntfy.sh/publish/), [subscribe to topics](https://docs.ntfy.sh/subscribe/cli/) as well as to self-host your own ntfy server. It's all pretty straight forward. Just install the binary, package or Docker image, configure it and run it. Just like any other software. No fuzz.

Info

The following steps are only required if you want to **self-host your own ntfy server or you want to use the ntfy CLI**. If you just want to [send messages using ntfy.sh](https://docs.ntfy.sh/publish/), you don't need to install anything. You can just use `curl`.

### General steps[¶](https://docs.ntfy.sh/install/#general-steps "Permanent link")

The ntfy server comes as a statically linked binary and is shipped as tarball, deb/rpm packages and as a Docker image. We support amd64, armv7 and arm64.

1. Install ntfy using one of the methods described below
2. Then (optionally) edit `/etc/ntfy/server.yml` for the server (Linux only, see [configuration](https://docs.ntfy.sh/config/) or [sample server.yml](https://github.com/binwiederhier/ntfy/blob/main/server/server.yml))
3. Or (optionally) create/edit `~/.config/ntfy/client.yml` (for the non-root user) or `/etc/ntfy/client.yml` (for the root user), see [sample client.yml](https://github.com/binwiederhier/ntfy/blob/main/client/client.yml))

To run the ntfy server, then just run `ntfy serve` (or `systemctl start ntfy` when using the deb/rpm). To send messages, use `ntfy publish`. To subscribe to topics, use `ntfy subscribe` (see [subscribing via CLI](https://docs.ntfy.sh/subscribe/cli/) for details).

If you like tutorials, check out  [Kris Occhipinti's ntfy install guide](https://www.youtube.com/watch?v=bZzqrX05mNU) on YouTube, or [Alex's Docker-based setup guide](https://blog.alexsguardian.net/posts/2023/09/12/selfhosting-ntfy/). Both are great resources to get started. _I am not affiliated with Kris or Alex, I just liked their video/post._

### Linux binaries[¶](https://docs.ntfy.sh/install/#linux-binaries "Permanent link")

Please check out the [releases page](https://github.com/binwiederhier/ntfy/releases) for binaries and deb/rpm packages.

x86_64/amd64

```bash
wget https://github.com/binwiederhier/ntfy/releases/download/v2.7.0/ntfy_2.7.0_linux_amd64.tar.gz 
tar zxvf ntfy_2.7.0_linux_amd64.tar.gz 
sudo cp -a ntfy_2.7.0_linux_amd64/ntfy /usr/local/bin/ntfy 
sudo mkdir /etc/ntfy && sudo cp ntfy_2.7.0_linux_amd64/{client,server}/*.yml /etc/ntfy 
sudo ntfy serve
```

### Debian/Ubuntu repository[¶](https://docs.ntfy.sh/install/#debianubuntu-repository "Permanent link")

Installation via Debian repository:

x86_64/amd64

```bash
sudo mkdir -p /etc/apt/keyrings 
curl -fsSL https://archive.heckel.io/apt/pubkey.txt | sudo gpg --dearmor -o /etc/apt/keyrings/archive.heckel.io.gpg 
sudo apt install apt-transport-https 
sudo sh -c "echo 'deb [arch=amd64 signed-by=/etc/apt/keyrings/archive.heckel.io.gpg] https://archive.heckel.io/apt debian main' \     > /etc/apt/sources.list.d/archive.heckel.io.list"   
sudo apt update 
sudo apt install ntfy 
sudo systemctl enable ntfy 
sudo systemctl start ntfy
```

Manually installing the .deb file:

x86_64/amd64

```bash
wget https://github.com/binwiederhier/ntfy/releases/download/v2.7.0/ntfy_2.7.0_linux_amd64.deb 
sudo dpkg -i ntfy_*.deb 
sudo systemctl enable ntfy 
sudo systemctl start ntfy
```

### Fedora/RHEL/CentOS[¶](https://docs.ntfy.sh/install/#fedorarhelcentos "Permanent link")

x86_64/amd64

```bash
sudo rpm -ivh https://github.com/binwiederhier/ntfy/releases/download/v2.7.0/ntfy_2.7.0_linux_amd64.rpm 
sudo systemctl enable ntfy  
sudo systemctl start ntfy
```

### Arch Linux[¶](https://docs.ntfy.sh/install/#arch-linux "Permanent link")

ntfy can be installed using an [AUR package](https://aur.archlinux.org/packages/ntfysh-bin/). You can use an [AUR helper](https://wiki.archlinux.org/title/AUR_helpers) like `paru`, `yay` or others to download, build and install ntfy and keep it up to date.

```bash
paru -S ntfysh-bin
```

Alternatively, run the following commands to install ntfy manually:

```bash
curl https://aur.archlinux.org/cgit/aur.git/snapshot/ntfysh-bin.tar.gz | tar xzv 
cd ntfysh-bin 
makepkg -si
```

### NixOS / Nix[¶](https://docs.ntfy.sh/install/#nixos-nix "Permanent link")

ntfy is packaged in nixpkgs as `ntfy-sh`. It can be installed by adding the package name to the configuration file and calling `nixos-rebuild`. Alternatively, the following command can be used to install ntfy in the current user environment:

```bash
nix-env -iA ntfy-sh
```

NixOS also supports [declarative setup of the ntfy server](https://search.nixos.org/options?channel=unstable&show=services.ntfy-sh.enable&from=0&size=50&sort=relevance&type=packages&query=ntfy).

### macOS[¶](https://docs.ntfy.sh/install/#macos "Permanent link")

The [ntfy CLI](https://docs.ntfy.sh/subscribe/cli/) (`ntfy publish` and `ntfy subscribe` only) is supported on macOS as well. To install, please [download the tarball](https://github.com/binwiederhier/ntfy/releases/download/v2.7.0/ntfy_2.7.0_darwin_all.tar.gz), extract it and place it somewhere in your `PATH` (e.g. `/usr/local/bin/ntfy`).

If run as `root`, ntfy will look for its config at `/etc/ntfy/client.yml`. For all other users, it'll look for it at `~/Library/Application Support/ntfy/client.yml` (sample included in the tarball).

```bash
curl -L https://github.com/binwiederhier/ntfy/releases/download/v2.7.0/ntfy_2.7.0_darwin_all.tar.gz > ntfy_2.7.0_darwin_all.tar.gz 
tar zxvf ntfy_2.7.0_darwin_all.tar.gz 
sudo cp -a ntfy_2.7.0_darwin_all/ntfy /usr/local/bin/ntfy 
mkdir ~/Library/Application\ Support/ntfy  
cp ntfy_2.7.0_darwin_all/client/client.yml ~/Library/Application\ Support/ntfy/client.yml 
ntfy --help
```

Info

Only the ntfy CLI is supported on macOS. ntfy server is currently not supported, but you can build and run it for development as well. Check out the [build instructions](https://docs.ntfy.sh/develop/) for details.

### Homebrew[¶](https://docs.ntfy.sh/install/#homebrew "Permanent link")

To install the [ntfy CLI](https://docs.ntfy.sh/subscribe/cli/) (`ntfy publish` and `ntfy subscribe` only) via Homebrew (Linux and macOS), simply run:

`brew install ntfy`

### Windows[¶](https://docs.ntfy.sh/install/#windows "Permanent link")

The [ntfy CLI](https://docs.ntfy.sh/subscribe/cli/) (`ntfy publish` and `ntfy subscribe` only) is supported on Windows as well. To install, please [download the latest ZIP](https://github.com/binwiederhier/ntfy/releases/download/v2.7.0/ntfy_2.7.0_windows_amd64.zip), extract it and place the `ntfy.exe` binary somewhere in your `%Path%`.

The default path for the client config file is at `%AppData%\ntfy\client.yml` (not created automatically, sample in the ZIP file).

Also available in [Scoop's](https://scoop.sh/) Main repository:

```shell
scoop install ntfy
```

Info

There is currently no installer for Windows, and the binary is not signed. If this is desired, please create a [GitHub issue](https://github.com/binwiederhier/ntfy/issues) to let me know.

### Docker[¶](https://docs.ntfy.sh/install/#docker "Permanent link")

The [ntfy image](https://hub.docker.com/r/binwiederhier/ntfy) is available for amd64, armv6, armv7 and arm64. It should be pretty straight forward to use.

The server exposes its web UI and the API on port 80, so you need to expose that in Docker. To use the persistent [message cache](https://docs.ntfy.sh/config/#message-cache), you also need to map a volume to `/var/cache/ntfy`. To change other settings, you should map `/etc/ntfy`, so you can edit `/etc/ntfy/server.yml`.

Info

Note that the Docker image **does not contain a `/etc/ntfy/server.yml` file**. If you'd like to use a config file, please manually create one outside the image and map it as a volume, e.g. via `-v /etc/ntfy:/etc/ntfy`. You may use the [`server.yml` file on GitHub](https://github.com/binwiederhier/ntfy/blob/main/server/server.yml) as a template.

Basic usage (no cache or additional config):

```bash
docker run -p 80:80 -it binwiederhier/ntfy serve
```

With persistent cache (configured as command line arguments):

```bash
docker run \   -v /var/cache/ntfy:/var/cache/ntfy \   -p 80:80 \   -it \   binwiederhier/ntfy \     serve \     --cache-file /var/cache/ntfy/cache.db
```

With other config options, timezone, and non-root user (configured via `/etc/ntfy/server.yml`, see [configuration](https://docs.ntfy.sh/config/) for details):

```shell
docker run \   -v /etc/ntfy:/etc/ntfy \   -e TZ=UTC \   -p 80:80 \   -u UID:GID \   -it \   binwiederhier/ntfy \   serve
```

Using docker-compose with non-root user and healthchecks enabled:

```shell
version: "2.3"  

services:   
	ntfy:     
		image: binwiederhier/ntfy     
		container_name: ntfy     
		command:       
			- serve     
		environment:       
			- TZ=UTC    # optional: set desired timezone     
		user: UID:GID # optional: replace with your own user/group or uid/gid     
		volumes:       
			- /var/cache/ntfy:/var/cache/ntfy       
			- /etc/ntfy:/etc/ntfy     
		ports:       
			- 80:80     
		healthcheck: # optional: remember to adapt the host:port to your environment         
			test: ["CMD-SHELL", "wget -q --tries=1 http://localhost:80/v1/health -O - | grep -Eo '\"healthy\"\\s*:\\s*true' || exit 1"]         
			interval: 60s         
			timeout: 10s         
			retries: 3         
			start_period: 40s     
		restart: unless-stopped
```

If using a non-root user when running the docker version, be sure to chown the server.yml, user.db, and cache.db files and attachments directory to the same uid/gid.

Alternatively, you may wish to build a customized Docker image that can be run with fewer command-line arguments and without delivering the configuration file separately.

```
FROM binwiederhier/ntfy 
COPY server.yml /etc/ntfy/server.yml 
ENTRYPOINT ["ntfy", "serve"]
```

This image can be pushed to a container registry and shipped independently. All that's needed when running it is mapping ntfy's port to a host port.

### Kubernetes[¶](https://docs.ntfy.sh/install/#kubernetes "Permanent link")

The setup for Kubernetes is very similar to that for Docker, and requires a fairly minimal deployment or pod definition to function. There are a few options to mix and match, including a deployment without a cache file, a stateful set with a persistent cache, and a standalone unmanned pod.

deployment

```
apiVersion: apps/v1 
kind: Deployment 
metadata:   
	name: ntfy 
spec:   
	selector:     
		matchLabels:       
			app: ntfy   
		template:     
			metadata:       
				labels:         
					app: ntfy     
			spec:       
				containers:       
					- name: ntfy         
					image: binwiederhier/ntfy         
					args: ["serve"]         
					resources:           
						limits:             
							memory: "128Mi"             
							cpu: "500m"         
					ports:         
					- containerPort: 80           
						name: http         
					volumeMounts:         
					- name: config           
						mountPath: "/etc/ntfy"           
						readOnly: true       
				volumes:         
					- name: config           
						configMap:             
							name: ntfy 
--- 
# Basic service for port 80 
apiVersion: v1 
kind: Service 
metadata:   
	name: ntfy 
spec:   
	selector:     
		app: ntfy   
	ports:   
	- port: 80     
		targetPort: 80
```
--- 
stateful set

```
apiVersion: apps/v1 
kind: StatefulSet 
metadata: 
	name: ntfy 
spec: 
	selector: 
		matchLabels: 
			app: ntfy 
	serviceName: ntfy 
	template: 
		metadata: 
			labels: 
				app: ntfy 
		spec: 
			containers: 
			- name: ntfy 
				image: binwiederhier/ntfy 
				args: ["serve", "--cache-file", "/var/cache/ntfy/cache.db"] 
				ports: 
				- containerPort: 80 
					name: http 
				volumeMounts: 
				- name: config 
					mountPath: "/etc/ntfy" 
					readOnly: true 
				- name: cache 
					mountPath: "/var/cache/ntfy" 
			volumes: 
				- name: config 
				configMap: 
					name: ntfy 
	volumeClaimTemplates: 
	- metadata: 
			name: cache 
		spec: accessModes: [ "ReadWriteOnce" ] 
			resources: 
				requests: 
					storage: 1Gi
```
---
pod
```
apiVersion: v1 
kind: Pod 
metadata: 
	labels: 
		app: ntfy 
spec: 
	containers: 
	- name: ntfy 
	  image: binwiederhier/ntfy 
	  args: ["serve"] 
	  resources: 
		  limits: 
			  memory: "128Mi" 
			  cpu: "500m" 
		ports: 
		- containerPort: 80 
		  name: http 
		volumeMounts: 
		- name: config 
		  mountPath: "/etc/ntfy" 
		  readOnly: true 
	volumes: 
		- name: config 
		  configMap: 
			  name: ntfy
```

Configuration is relatively straightforward. As an example, a minimal configuration is provided.

resource definition

```
apiVersion: v1 
kind: ConfigMap 
metadata:   
	name: ntfy 
data:   
	server.yml: |     
		# Template: https://github.com/binwiederhier/ntfy/blob/main/server/server.yml     base-url: https://ntfy.sh
```
from-file
```bash
kubectl create configmap ntfy --from-file=server.yml 
```

### Kustomize[¶](https://docs.ntfy.sh/install/#kustomize "Permanent link")

ntfy can be deployed in a Kubernetes cluster with [Kustomize](https://github.com/kubernetes-sigs/kustomize), a tool used to customize Kubernetes objects using a `kustomization.yaml` file.

1. Create new folder - `ntfy`
2. Add all files listed below
    1. `kustomization.yaml` - stores all configmaps and resources used in a deployment
    2. `ntfy-deployment.yaml` - define deployment type and its parameters
    3. `ntfy-pvc.yaml` - describes how [persistent volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) will be created
    4. `ntfy-svc.yaml` - expose application to the internal kubernetes network
    5. `ntfy-ingress.yaml` - expose service to outside the network using [ingress controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/)
    6. `server.yaml` - simple server configuration
3. Replace **TESTNAMESPACE** within `kustomization.yaml` with designated namespace
4. Replace **ntfy.test** within `ntfy-ingress.yaml` with desired DNS name
5. Apply configuration to cluster set in current context:

```bash
kubectl apply -k /ntfy
```

kustomization.yamlntfy-deployment.yamlntfy-pvc.yamlntfy-svc.yamlntfy-ingress.yamlserver.yml

```
apiVersion: kustomize.config.k8s.io/v1beta1 
kind: Kustomization 
resources:   
	- ntfy-deployment.yaml # deployment definition   
	- ntfy-svc.yaml # service connecting pods to cluster network   
	- ntfy-pvc.yaml # pvc used to store cache and attachment   
	- ntfy-ingress.yaml # ingress definition 
configMapGenerator: # will parse config from raw config to configmap,it allows for dynamic reload of application if additional app is deployed ie https://github.com/stakater/Reloader     
	- name: server-config       
	  files:          
		  - server.yml 
namespace: TESTNAMESPACE # select namespace for whole application
```
# Other doc
![](https://www.youtube.com/watch?v=poDIT2ruQ9M)