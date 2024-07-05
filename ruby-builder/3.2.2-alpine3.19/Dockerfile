FROM --platform=linux/amd64 ruby:3.2.2-alpine3.19

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to build proyects with ruby"
LABEL version="3.2.2-alpine3.19"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  busybox=1.36.1-r19 \
  ssl_client=1.36.1-r19 \
  openssl=3.1.6-r0 \
  tar=1.35-r2 \
  build-base=0.5-r3 \
  tzdata=2024a-r0 \
  nodejs=20.12.1-r0 \
  yarn=1.22.19-r0 \
  git=2.43.4-r0 \
  musl=1.2.4_git20230717-r4 \
  ruby-full=3.2.4-r0 \
  ruby-dev=3.2.4-r0 \
  gcc=13.2.1_git20231014-r0 \
  make=4.4.1-r2 \
  musl-dev=1.2.4_git20230717-r4 \
  openssl-dev=3.1.6-r0 \
  g++=13.2.1_git20231014-r0 \
  linux-headers=6.5-r0 \
  xz=5.4.5-r0 \
  vips=8.15.0-r0 \
  imagemagick=7.1.1.32-r0 \
  postgresql15-client=15.7-r0 \
  postgresql15-dev=15.7-r0
