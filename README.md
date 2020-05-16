# Hash

Docker container with utilities to compute hashes (CRC32, MD5, SHA-1, SHA-256, SHA-512, Argon2...).

![GitHub Build](https://img.shields.io/github/workflow/status/thomasleplus/docker-hash/Docker%20Image%20CI)
![Docker Stars](https://img.shields.io/docker/stars/thomasleplus/hash)
![Docker Pulls](https://img.shields.io/docker/pulls/thomasleplus/hash)
![Docker Automated](https://img.shields.io/docker/cloud/automated/thomasleplus/hash)
![Docker Build](https://img.shields.io/docker/cloud/build/thomasleplus/hash)

## Example not using the filesystem

Let's say that you have a file `foo.txt` in your current working directory that you want to compute its SHA-256 hash:

### Mac/Linux

```
cat foo.txt | docker run --rm -i --net=none thomasleplus/hash sha256sum
```

### Windows

```
type foo.txt | docker run --rm -i --net=none thomasleplus/hash sha256sum
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.txt` in your current working directory that you want to compute its SHA-256 hash:

### Mac/Linux

```
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/hash sha256sum /tmp/foo.txt
```

### Windows

In `cmd`:

```
docker run --rm -t --net=none -v "%cd%:/tmp" thomasleplus/hash sha256sum /tmp/foo.txt
```

In PowerShell:

```
docker run --rm -t --net=none -v "${PWD}:/tmp" thomasleplus/hash sha256sum /tmp/foo.txt
```

## Help

To know what are the message digest algorithms supported by `openssl`, you can run:

```
docker run --rm --net=none thomasleplus/hash openssl help
```

## Request new tool

Please use [this link](https://github.com/thomasleplus/docker-hash/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
