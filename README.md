# Hash

Docker container with utilities to compute hashes (CRC32, MD5, SHA-1, SHA-256, SHA-512, Argon2...).

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
