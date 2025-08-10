# Install ghost
## Supported tags and respective `Dockerfile` links

- [`5.75.3`, `5.75`, `5`, `latest`](https://github.com/docker-library/ghost/blob/4bc4a3be710e4f897989ff16f4685fb62730b6c2/5/debian/Dockerfile)
- [`5.75.3-alpine`, `5.75-alpine`, `5-alpine`, `alpine`](https://github.com/docker-library/ghost/blob/4bc4a3be710e4f897989ff16f4685fb62730b6c2/5/alpine/Dockerfile)

## Quick reference (cont.)

- **Where to file issues**:  
    [https://github.com/docker-library/ghost/issues](https://github.com/docker-library/ghost/issues?q=)
    
- **Supported architectures**: ([more info](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
    [`amd64`](https://hub.docker.com/r/amd64/ghost/), [`arm32v6`](https://hub.docker.com/r/arm32v6/ghost/), [`arm32v7`](https://hub.docker.com/r/arm32v7/ghost/), [`arm64v8`](https://hub.docker.com/r/arm64v8/ghost/), [`ppc64le`](https://hub.docker.com/r/ppc64le/ghost/), [`s390x`](https://hub.docker.com/r/s390x/ghost/)
    
- **Published image artifact details**:  
    [repo-info repo's `repos/ghost/` directory](https://github.com/docker-library/repo-info/blob/master/repos/ghost) ([history](https://github.com/docker-library/repo-info/commits/master/repos/ghost))  
    (image metadata, transfer size, etc)
    
- **Image updates**:  
    [official-images repo's `library/ghost` label](https://github.com/docker-library/official-images/issues?q=label%3Alibrary%2Fghost)  
    [official-images repo's `library/ghost` file](https://github.com/docker-library/official-images/blob/master/library/ghost) ([history](https://github.com/docker-library/official-images/commits/master/library/ghost))
    
- **Source of this description**:  
    [docs repo's `ghost/` directory](https://github.com/docker-library/docs/tree/master/ghost) ([history](https://github.com/docker-library/docs/commits/master/ghost))
    

## Ghost

Ghost is a free and open source blogging platform written in JavaScript and distributed under the MIT License, designed to simplify the process of online publishing for individual bloggers as well as online publications.

> [wikipedia.org/wiki/Ghost_(blogging_platform)](http://en.wikipedia.org/wiki/Ghost_%28blogging_platform%29)

![logo](https://raw.githubusercontent.com/docker-library/docs/c5b6d94dc8f0557925ab37ca43141c0efc5cc363/ghost/logo.png)

## How to use this image

This will start a Ghost development instance listening on the default Ghost port of 2368.

```console
$ docker run -d --name some-ghost -e NODE_ENV=development ghost
```

### Custom port

If you'd like to be able to access the instance from the host without the container's IP, standard port mappings can be used:

```console
$ docker run -d --name some-ghost -e NODE_ENV=development -e url=http://localhost:3001 -p 3001:2368 ghost
```

If all goes well, you'll be able to access your new site on `http://localhost:3001` and `http://localhost:3001/ghost` to access Ghost Admin (or `http://host-ip:3001` and `http://host-ip:3001/ghost`, respectively).

#### Upgrading Ghost

You will want to ensure you are running the latest minor version of Ghost before upgrading major versions. Otherwise, you may run into database errors.

For upgrading your Ghost container you will want to mount your data to the appropriate path in the predecessor container (see below): import your content from the admin panel, stop the container, and then re-mount your content to the successor container you are upgrading into; you can then export your content from the admin panel.

### Stateful

Mount your existing content. In this example we also use the Alpine Linux based image.

```console
$ docker run -d \
	--name some-ghost \
	-e NODE_ENV=development \
	-e database__connection__filename='/var/lib/ghost/content/data/ghost.db' \
	-p 3001:2368 \
	-v /path/to/ghost/blog:/var/lib/ghost/content \
	ghost:alpine
```

Note: `database__connection__filename` is only valid in development mode and is the location for the SQLite database file. If using development mode, it should be set to a writeable path within a persistent folder (bind mount or volume). It is not available in production mode because an external MySQL server is required (see the `docker-compose` example below).

#### Docker Volume

Alternatively you can use a named [docker volume](https://docs.docker.com/storage/volumes/) instead of a direct host path for `/var/lib/ghost/content`:

```console
$ docker run -d \
	--name some-ghost \
	-e NODE_ENV=development \
	-e database__connection__filename='/var/lib/ghost/content/data/ghost.db' \
	-p 3001:2368 \
	-v some-ghost-data:/var/lib/ghost/content \
	ghost
```

### Configuration

All Ghost configuration parameters (such as `url`) can be specified via environment variables. See [the Ghost documentation](https://ghost.org/docs/concepts/config/#running-ghost-with-config-env-variables) for details about what configuration is allowed and how to convert a nested configuration key into the appropriate environment variable name:

```console
$ docker run -d --name some-ghost -e NODE_ENV=development -e url=http://some-ghost.example.com ghost
```

(There are further configuration examples in the `stack.yml` listed below.)

### What is the Node.js version?

When opening a ticket at [https://github.com/TryGhost/Ghost/issues](https://github.com/TryGhost/Ghost/issues) it becomes necessary to know the version of Node.js in use:

```console
$ docker exec <container-id> node --version
[node version output]
```

### Note about Ghost-CLI

While the Docker images do have Ghost-CLI available and do use some of its commands to set up the base Ghost image, many of the other Ghost-CLI commands won't work correctly, and really aren't designed/intended to. For more info see [docker-library/ghost#156 (comment)](https://github.com/docker-library/ghost/issues/156#issuecomment-428159861)

### Production mode

To run Ghost for production you'll also need to be running with MySQL 8, https, and a reverse proxy configured with appropriate `X-Forwarded-For`, `X-Forwarded-Host`, and `X-Forwarded-Proto` (`https`) headers.

The following example demonstrates some of the necessary configuration for running with MySQL. For more detail, see [Ghost's "Configuration options" documentation](https://ghost.org/docs/config/#configuration-options).

### ... via [`docker-compose`](https://github.com/docker/compose) or [`docker stack deploy`](https://docs.docker.com/engine/reference/commandline/stack_deploy/)

Example `docker-compose.yml` for `ghost`:

```yaml
version: '3.1'

services:

  ghost:
    image: ghost:5-alpine
    restart: always
    ports:
      - 8080:2368
    environment:
      # see https://ghost.org/docs/config/#configuration-options
      database__client: mysql
      database__connection__host: db
      database__connection__user: root
      database__connection__password: example
      database__connection__database: ghost
      # this url value is just an example, and is likely wrong for your environment!
      url: http://localhost:8080
      # contrary to the default mentioned in the linked documentation, this image defaults to NODE_ENV=production (so development mode needs to be explicitly specified if desired)
      #NODE_ENV: development
    volumes:
      - ghost:/var/lib/ghost/content

  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: example
    volumes:
      - db:/var/lib/mysql

volumes:
  ghost:
  db:
```


Run `docker stack deploy -c stack.yml ghost` (or `docker-compose -f stack.yml up`), wait for it to initialize completely, and visit `http://swarm-ip:8080`, `http://localhost:8080`, or `http://host-ip:8080` (as appropriate).

## Image Variants

The `ghost` images come in many flavors, each designed for a specific use case.

### `ghost:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of.

### `ghost:<version>-alpine`

This image is based on the popular [Alpine Linux project](https://alpinelinux.org), available in [the `alpine` official image](https://hub.docker.com/_/alpine). Alpine Linux is much smaller than most distribution base images (~5MB), and thus leads to much slimmer images in general.

This variant is useful when final image size being as small as possible is your primary concern. The main caveat to note is that it does use [musl libc](https://musl.libc.org) instead of [glibc and friends](https://www.etalabs.net/compare_libcs.html), so software will often run into issues depending on the depth of their libc requirements/assumptions. See [this Hacker News comment thread](https://news.ycombinator.com/item?id=10782897) for more discussion of the issues that might arise and some pro/con comparisons of using Alpine-based images.

To minimize image size, it's uncommon for additional related tools (such as `git` or `bash`) to be included in Alpine-based images. Using this image as a base, add the things you need in your own Dockerfile (see the [`alpine` image description](https://hub.docker.com/_/alpine/) for examples of how to install packages if you are unfamiliar).


# Back up your data

## Prerequisites

If your self-hosted site is running an older major version of Ghost, you may need to update. Check the latest [version of Ghost on GitHub](https://github.com/TryGhost/Ghost/releases), and follow this [upgrade guide](https://ghost.org/docs/update/).

## General
The first step towards moving from your own self-hosted Ghost instance to Ghost(Pro) is to retrieve all of your data from your server to your local machine. It’s best to do this first, to ensure you have a backup in place.

> The commands in this guide assume you followed our [Ubuntu guide](https://ghost.org/docs/install/ubuntu/) to set up your own instance. If you used another method, you’ll need to adapt the paths in the commands to suit.

### Exporting content

Log into Ghost Admin for your self-hosted in production and navigate to the **Labs** view, and click **Export** to download your content. This will be `.json` file, with a name like `my-site.ghost.2020-09-30-14-15-49.json`.

![content import export](https://ghost.org/images/docs/migration/self-hosted/ghost-content-import-export_hu272562aa500e83b9baeec6c17282ce1a_25089_1628x0_resize_q100_h2_box_3.webp)

### Routes and redirects

Staying on the **Labs** page, click **Download current redirects** to get your redirects file. This will be called `redirects.yaml` (or `redirects.json` depending on your Ghost version). If you’re using custom routes, click **Download current routes.yaml** to get your `routes.yaml` file.

![routes redirects](https://ghost.org/images/docs/migration/self-hosted/ghost-route-redirects_hu954a63ee77a86db320db7d009e6fb2e9_29801_1628x0_resize_q100_h2_box_3.webp)

### Themes

Navigate to the **Design** view, and click the **Download** button next to the Active label export your current theme. This will be a `.zip` file. Optionally, if you have other themes that you’d like to save, download them and back them up.

![themes settings](https://ghost.org/images/docs/migration/self-hosted/ghost-themes-settings_hu3b859fed207678d52a22902f80176aaf_12909_1628x0_resize_q100_h2_box_3.webp)

### Images

To download your images, you’ll need shell access to your server. If you’re unable to gain shell access to your current web host, you may need to contact their support team and ask for a zip of your images directory.

Once you’re logged in to your server, `cd` to the `content` directory:

```bash
cd /var/www/ghost/content
```

And then `zip` the `images` directory with all its contents:

```bash
zip -r images.zip images/*
```

Ensure your `images` folder only contains images. Any other file types may cause import errors.

Now we need to get that zip file from your server onto your local machine:

```bash
scp user@123.456.789.123:/var/www/ghost/content/images.zip ~/Desktop/images.zip
```

The folder structure should look like this, with `images` being the only top-level folder once unzipped:

![images in finder](https://ghost.org/images/docs/migration/self-hosted/images-in-finder_huf248f9006ca4711e6e56a11852458172_99427_1260x0_resize_q100_h2_box.webp)

## Uploading to Ghost(Pro)

Once you’ve retrieved all of these exports, you can upload them to Ghost(Pro) in the same order.

### Content

Log into your new Ghost(Pro) site, and head to the **Labs** view. Next to the **Import content** header, select your content `.json` file and click **Import**.

![user import successful](https://ghost.org/images/docs/migration/self-hosted/ghost-import-successful_huade8b63d13532484da2176e269d2dc02_38287_1628x0_resize_q100_h2_box_3.webp)

### Routes and Redirects

Staying on the **Labs** view, click **Upload redirects JSON**, then select your `redirects.json` file to upload it. Then click **Upload routes YAML**, select your `routes.yaml` file to upload that.

### Themes

Head over to the **Design** view, and click **Upload a theme**, select your theme `.zip` file, and activate it.

![activate theme](https://ghost.org/images/docs/migration/self-hosted/ghost-theme-upload_huf4a027a768e71e6bd93af4733d14943e_23711_1226x0_resize_q100_h2_box_3.webp)

### Images

The final step is to upload your images. The best way to approach this depends on how big your `images.zip` file is. A large file will take longer to upload and process.

If your file is less than 500mb, you can upload this zip in the same way you uploaded your content JSON file. If the file is larger, it’s recommended to split it into multiple smaller files, whilst retaining the folder structure.

If you have a large image directory or encounter any errors, contact support so we can help upload your images.