FROM alpine:3.24.0@sha256:a2d49ea686c2adfe3c992e47dc3b5e7fa6e6b5055609400dc2acaeb241c829f4

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    apache2-utils=2.4.67-r0 \
    argon2=20190702-r5 \
    coreutils=9.11-r0 \
    curl=8.20.0-r1 \
    git=2.54.0-r0 \
    openssl=3.5.7-r0 \
    outils-sha256=0.14-r0 \
    perl-archive-zip=1.68-r3 \
    perl-utils=5.42.2-r0 \
    py3-pip=26.1.2-r0 \
    python3=3.14.5-r0 \
    rhash=1.4.6-r0 \
    xxhash=0.8.3-r1 \
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
