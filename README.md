# Hash

Docker container with utilities to compute hashes (CRC32, MD5, SHA-1, SHA-256, SHA-512, Argon2...).

## Example

Assuming that you have a file `foo.txt` in your current working directory that you want to compute its SHA-256 hash:

### Mac/Linux

```
$ cat foo.txt | docker run --rm -i --net=none thomasleplus/hash sha256sum
```

### Windows


```
$ type foo.txt | docker run --rm -i --net=none thomasleplus/hash sha256sum
```

## Help

To know what are the message digest algorithms supported by `openssl`, you can run:

```
$ docker run --rm --net=none thomasleplus/hash openssl help
```
