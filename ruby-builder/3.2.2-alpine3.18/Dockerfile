FROM --platform=linux/amd64 ruby:3.2.2-alpine3.18

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to build proyects with ruby"
LABEL version="3.2.2-alpine3.18"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  busybox=1.36.1-r7 \
  ssl_client=1.36.1-r7 \
  openssl=3.1.6-r0 \
  tar=1.34-r3 \
  build-base=0.5-r3 \
  tzdata=2024a-r0 \
  nodejs=18.20.1-r0 \
  yarn=1.22.19-r0 \
  git=2.40.1-r0 \
  musl=1.2.4-r2 \
  ruby-full=3.2.4-r0 \
  ruby-dev=3.2.4-r0 \
  gcc=12.2.1_git20220924-r10 \
  make=4.4.1-r1 \
  musl-dev=1.2.4-r2 \
  openssl-dev=3.1.6-r0 \
  g++=12.2.1_git20220924-r10 \
  linux-headers=6.3-r0 \
  xz=5.4.3-r0 \
  vips=8.14.3-r0 \
  imagemagick=7.1.1.13-r1 \
  postgresql15-client=15.7-r0 \
  postgresql15-dev=15.7-r0
