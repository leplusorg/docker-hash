FROM alpine:3.22.0@sha256:8a1f59ffb675680d47db6337b49d22281a139e9d709335b492be023728e11715

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

# hadolint ignore=DL3019
RUN apk -U upgrade \
    && apk add \
    apache2-utils=2.4.63-r4 \
    argon2=20190702-r5 \
    coreutils=9.7-r1 \
    curl=8.14.1-r1 \
    git=2.49.0-r0 \
    openssl=3.5.0-r0 \
    perl-archive-zip=1.68-r3 \
    perl-utils=5.40.2-r0 \
    py3-pip=25.1.1-r0 \
    python3=3.12.11-r0 \
    rhash=1.4.5-r0 \
    xxhash=0.8.3-r0 \
    && if apk -u list | grep -q -e . ; then \
      apk -u list ; \
      exit 1 ; \
    fi \
    && apk cache clean \
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
