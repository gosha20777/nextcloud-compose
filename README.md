# Nextcloud with Docker compose

This repository contains a Docker compose file which can be used to easily create a Nextcloud instance.

- Fully-featured Nextcloud instance backed by a MySQL database
- Automatic SSL certificate issuance and renewal (using [`nginx-proxy-letsencrypt-companion`](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion))

## Architecture

Here are the various containers involved.

- `nextcloud`: the actual Nextcloud server
- `mysql`: the database used by Nextcloud to store its configuration
- `reverse-proxy`: a nginx reverse proxy in front of Nextcloud and doing SSL termination
- `letsencrypt-companion`: an utility container which issues and renews SSL certificates

## Usage

Follow the steps below.

### Step 1: Configuration

Edit the `.env` file, and change at least the following:

- `HOST`: the hostname of your server (e.g. `nextcloud.yandex.ru`).
- `DATA_DIR`: the location of the data (e.g. `/files/nextcloud`)

### Step 2: Profit!

Run:

```
$ docker-compose up -d
```

You'll need to wait a few minutes on first launch, as there is some certificate generation involved. Then, you should be able to access your Nextcloud instance!