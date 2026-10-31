FROM alpine:3.24.3@sha256:be2656061b536c1883c4034790e21d0a09c5aaaf51968b89368a3c0371ea2c9a

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    apache2-utils=2.4.69-r0 \
    argon2=20190702-r5 \
    coreutils=9.11-r0 \
    curl=8.23.0-r0 \
    git=2.54.0-r0 \
    openssl=3.5.9-r0 \
    outils-sha256=0.14-r0 \
    perl-archive-zip=1.68-r3 \
    perl-utils=5.42.2-r1 \
    py3-pip=26.1.2-r0 \
    python3=3.14.10-r1 \
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
