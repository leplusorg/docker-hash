# Hash

Docker container with utilities to compute hashes.

## Example

Assuming that you have a file `foo.txt` in your current working directory that you want to compute its SHA-256 hash:

### Mac/Linux

```
$ docker run --rm -it --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/hash sha256sum /tmp/foo.txt
```

### Windows

In `cmd`:

```
$ docker run --rm -it --net=none -v "%cd%:/tmp" thomasleplus/hash sha256sum /tmp/foo.txt
```

In PowerShell:

```
$ docker run --rm -it --net=none -v "${PWD}:/tmp" thomasleplus/hash sha256sum /tmp/foo.txt
```

## Help

To know more command line options of `hashlint`:

```
$ docker run --rm -it --net=none thomasleplus/hash sha256sum -h
```
