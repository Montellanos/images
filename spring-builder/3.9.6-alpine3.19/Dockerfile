ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM maven:3.9.6-eclipse-temurin-22-alpine

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to compile spring based proyects"
LABEL version="3.9.6-alpine3.19"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  git=2.43.6-r0 \
  xmlstarlet=1.6.1-r2 \
  libcrypto3=3.1.7-r1 \
  libssl3=3.1.7-r1 \
  busybox=1.36.1-r19 \
  curl=8.11.1-r0 \
  libcurl=8.11.1-r0 \
  libexpat=2.6.4-r0
