# uwegerdes/baseimage

A common base image for my Dockerfiles to save some disk space and build time.

The base for this image is ubuntu:latest but it might change in the future.

## Building with settings

If you want to build it with other settings load the Dockerfile in an empty directory, perhaps edit it to your needs.

If you run an apt-cacher-ng proxy server in your local network provide the address (if on your pc `hostname -i` should work).

It also has the timezone parameter, here set to `Europe/Berlin`.

Build it with (mind the dot in the last line):

```bash
$ docker build -t uwegerdes/baseimage \
	--build-arg APT_PROXY="http://$(hostname -i):3142" \
	--build-arg TZ="Europe/Berlin" \
	.
```

Check the `hostname -i` or change it to an address available in your local networt (not localhost) or omit the APT_PROXY line in the command above.
