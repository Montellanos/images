ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM node:22.11.0-alpine3.20

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on node"
LABEL version="22.11.0-alpine3.20"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  jq=1.7.1-r0 \
  git=2.45.2-r0 \
  libcrypto3=3.3.2-r1 \
  libssl3=3.3.2-r1 \
  libcurl=8.11.1-r0

RUN npm install -g npm@11.0.0 && \
  npm cache clean --force  