ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM alpine:3.21.3

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx"
LABEL version="1.26.2-alpine3.21"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.26.2-r4

RUN apk update && apk add --no-cache \
  nginx=${NGINX_VERSION} \
  nginx-mod-http-headers-more=${NGINX_VERSION} \
  libcrypto3=3.3.3-r0 \
  libssl3=3.3.3-r0 \
  musl=1.2.5-r9 \
  musl-utils=1.2.5-r9

COPY ./default.conf /etc/nginx/http.d/default.conf
COPY ./html /etc/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
