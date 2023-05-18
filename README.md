# Docker uwegerdes/baseimage

A common base image for my Dockerfiles to save some disk space and build time.

The base for this image is ubuntu:latest but it might change in the future.

## Install Docker

For Windows or Mac users: open [https://www.docker.com/get-started](https://www.docker.com/get-started) in your browser.

### Linux users: install Docker with:

```bash
curl -sSL https://get.docker.com | sh
sudo adduser [yourusername] docker
```

## Building with settings

If you want to build it with other settings load the Dockerfile in an empty directory, perhaps edit it to your needs.

If you have an apt-cacher-ng proxy server (try [uwegerdes/apt-cacher-ng](https://github.com/UweGerdes/docker-apt-cacher-ng)) you should check `hostname -i` or change it to an address available in your local networt (not localhost) or omit the APT_PROXY line in the command above.

There is also a timezone parameter for the baseimage, here set to `Europe/Berlin`.

Build the image with (mind the dot in the last line):

```bash
$ docker build -t uwegerdes/baseimage \
	-t uwegerdes/baseimage:2022-08-21 \
	--build-arg APT_PROXY="http://$(hostname -i):3142" \
	--build-arg TZ="Europe/Berlin" \
	--build-arg TERM="${TERM}" \
	.
```

## Usage

Use this baseimage in other `Dockerfile`s:

```
FROM uwegerdes/baseimage
```

## Settings

The build-args are saved and used by all images depending on this image.

