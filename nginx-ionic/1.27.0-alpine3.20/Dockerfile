ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM alpine:3.20.3

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx and ionic"
LABEL version="1.27.0-alpine3.20"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.27.0
ENV NGX_CONF_BUFFER_SIZE=8192
ENV HEADERS_MORE_NGINX_MODULE_VERSION=0.37

RUN apk update && apk add --no-cache \
  wget=1.24.5-r0 \
  build-base=0.5-r3\
  libcrypto3=3.3.2-r0 \
  libssl3=3.3.2-r0 \
  openssl-dev=3.3.2-r0 \ 
  pcre-dev=8.45-r3 \
  zlib-dev=1.3.1-r1 \
  busybox=1.36.1-r29

RUN wget --no-verbose https://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz \
  && tar -xzvf nginx-${NGINX_VERSION}.tar.gz \
  && wget --no-verbose https://github.com/openresty/headers-more-nginx-module/archive/v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && tar -xzvf v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && cd nginx-${NGINX_VERSION} \
  && sed -i "s/#define NGX_CONF_BUFFER .*/#define NGX_CONF_BUFFER $NGX_CONF_BUFFER_SIZE/" src/core/ngx_conf_file.c \
  && ./configure --with-http_ssl_module --with-compat --add-dynamic-module=../headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION} \
  && make modules -s \
  && make install -s \
  && cd .. \
  && rm -rf nginx-${NGINX_VERSION}.tar.gz nginx-${NGINX_VERSION} v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION}

RUN ln -s /usr/local/nginx/sbin/nginx /usr/local/bin/nginx

COPY ./default.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
