# Hash

Docker container with utilities to compute hashes (CRC32, MD5, SHA-1, SHA-256, SHA-512, Argon2...).

[![Docker Build](https://github.com/leplusorg/docker-hash/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-hash/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/hash)](https://hub.docker.com/r/leplusorg/hash)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/hash)](https://hub.docker.com/r/leplusorg/hash)
[![Docker Automated](https://img.shields.io/docker/cloud/automated/leplusorg/hash)](https://hub.docker.com/r/leplusorg/hash)
[![Docker Build](https://img.shields.io/docker/cloud/build/leplusorg/hash)](https://hub.docker.com/r/leplusorg/hash)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/hash?sort=semver)](https://hub.docker.com/r/leplusorg/hash)

## Example not using the filesystem

Let's say that you have a file `foo.txt` in your current working directory that you want to compute its SHA-256 hash:

**Mac/Linux**

```bash
cat foo.txt | docker run --rm -i --net=none leplusorg/hash sha256sum
```

**Windows**

```batch
type foo.txt | docker run --rm -i --net=none leplusorg/hash sha256sum
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.txt` in your current working directory that you want to compute its SHA-256 hash:

**Mac/Linux**

```bash
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" leplusorg/hash sha256sum /tmp/foo.txt
```

**Windows**

In `cmd`:

```batch
docker run --rm -t --net=none -v "%cd%:/tmp" leplusorg/hash sha256sum /tmp/foo.txt
```

In PowerShell:

```pwsh
docker run --rm -t --net=none -v "${PWD}:/tmp" leplusorg/hash sha256sum /tmp/foo.txt
```

## Help

To know what are the message digest algorithms supported by `openssl`, you can run:

```bash
docker run --rm --net=none leplusorg/hash openssl help
```

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-hash/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
