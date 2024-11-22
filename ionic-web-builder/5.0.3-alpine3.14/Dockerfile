ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM alpine:3.14.10

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Ubuntu based image to compile ionic web based proyects"
LABEL version="5.0.3-alpine3.14"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  nodejs=14.21.3-r0 \
  npm=7.17.0-r0 \
  git=2.32.7-r0

RUN npm install -g npm@6.14.8

RUN npm cache clean --force

RUN npm i -g ionic@5.0.3
RUN npm i -g cordova@11.0.0
