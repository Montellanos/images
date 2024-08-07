ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM alpine:3.20.1

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx"
LABEL version="1.26.1-alpine3.20"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.26.1-r0

RUN apk update && apk add --no-cache \
  nginx=${NGINX_VERSION} \
  nginx-mod-http-headers-more=${NGINX_VERSION} \
  libcrypto3=3.3.1-r3 \
  libssl3=3.3.1-r3

COPY ./default.conf /etc/nginx/http.d/default.conf
COPY ./html /etc/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
