ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM node:20.15.1-alpine3.20

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on node"
LABEL version="20.15.1-alpine3.20"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  jq=1.7.1-r0 \
  git=2.45.3-r0 \
  libcrypto3=3.3.3-r0 \
  libssl3=3.3.3-r0 \
  libcurl=8.12.1-r0 \
  musl=1.2.5-r1 \
  musl-utils=1.2.5-r1

RUN npm install -g npm@10.9.2 && \
  npm cache clean --force