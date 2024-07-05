FROM --platform=linux/amd64 ruby:3.3.3-alpine3.20

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to build proyects with ruby"
LABEL version="3.3.3-alpine3.20"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  openssl=3.3.1-r1 \
  tar=1.35-r2 \
  build-base=0.5-r3 \
  tzdata=2024a-r1 \
  nodejs=20.13.1-r0 \
  yarn=1.22.22-r0 \
  git=2.45.2-r0 \
  musl=1.2.5-r0 \
  ruby-full=3.3.3-r0 \
  ruby-dev=3.3.3-r0 \
  gcc=13.2.1_git20240309-r0 \
  make=4.4.1-r2 \
  musl-dev=1.2.5-r0 \
  openssl-dev=3.3.1-r1 \
  g++=13.2.1_git20240309-r0 \
  linux-headers=6.6-r0 \
  xz=5.6.1-r3 \
  vips=8.15.2-r1 \
  imagemagick=7.1.1.32-r2 \
  postgresql16-client=16.3-r0 \
  postgresql16-dev=16.3-r0
