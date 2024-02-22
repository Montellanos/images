FROM alpine:3.19.1

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx and ionic"
LABEL version="1.24.0-alpine3.19"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.24.0-r15

RUN apk update && apk add --no-cache \
  nginx=${NGINX_VERSION} \
  nginx-mod-http-headers-more=${NGINX_VERSION}

COPY ./default.conf /etc/nginx/http.d/default.conf
COPY ./html /etc/nginx/html