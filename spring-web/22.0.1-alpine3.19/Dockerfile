FROM eclipse-temurin:22.0.1_8-jre-alpine

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to expose spring web based proyects"
LABEL version="22.0.1-alpine3.19"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  libcrypto3=3.1.5-r0  \
  libssl3=3.1.5-r0 \
  busybox=1.36.1-r18