ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM node:16.20.2-alpine3.18

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on node"
LABEL version="16.20.2-alpine3.18"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  busybox=1.36.1-r7 \
  libcrypto3=3.1.8-r0 \
  libssl3=3.1.8-r0 \
  ssl_client=1.36.1-r7 \
  jq=1.6-r4 \
  musl=1.2.4-r3 \
  musl-utils=1.2.4-r3
