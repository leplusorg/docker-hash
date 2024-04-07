FROM alpine:3.19.1

# hadolint ignore=DL3018
RUN apk --update --no-cache add apache2-utils argon2 coreutils openssl perl-archive-zip perl-utils rhash xxhash \
    && rm -rf /var/cache/apk/*
