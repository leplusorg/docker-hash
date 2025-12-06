FROM alpine:3.23.0@sha256:51183f2cfa6320055da30872f211093f9ff1d3cf06f39a0bdb212314c5dc7375

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    apache2-utils=2.4.65-r0 \
    argon2=20190702-r5 \
    coreutils=9.7-r1 \
    curl=8.14.1-r2 \
    git=2.52.0-r0 \
    openssl=3.5.4-r0 \
    outils-sha256=0.14-r0 \
    perl-archive-zip=1.68-r3 \
    perl-utils=5.42.0-r0 \
    py3-pip=25.1.1-r1 \
    python3=3.12.12-r0 \
    rhash=1.4.6-r0 \
    xxhash=0.8.3-r0 \
    && apk cache --no-cache clean \
    && rm -rf /var/cache/apk/*

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

USER "${USER_NAME}"

ENV HOME="${USER_HOME}"

WORKDIR "${HOME}"
