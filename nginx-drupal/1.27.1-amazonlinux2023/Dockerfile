ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM amazonlinux:2023

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Amazonlinux 2023 based image to create containers based on nginx and drupal"
LABEL version="1.27.1-amazonlinux2023"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.27.1
ENV HEADERS_MORE_NGINX_MODULE_VERSION=0.37
ENV PHP_VERSION=8.3.10-1.amzn2023.0.1
ENV COMPOSER_VERSION=2.8.5
ENV XDEBUG_VERSION=3.3.2

RUN yum update -y -q \
  && yum install -y -q \
  curl-minimal-8.5.0-1.amzn2023.0.4 \
  git-2.40.1-1.amzn2023.0.3 \
  jq-1.7.1-48.amzn2023.0.1 \
  unzip-6.0-57.amzn2023.0.2 \
  tar-1.34-1.amzn2023.0.4 \
  make-4.3-5.amzn2023.0.2 \
  gcc-c++-11.4.1-2.amzn2023.0.2 \
  pcre-devel-8.44-3.amzn2023.1.0.3 \
  zlib-devel-1.2.11-33.amzn2023.0.5 \
  gcc-11.4.1-2.amzn2023.0.2 \
  autoconf-2.69-36.amzn2023.0.3 \
  openssl-3.0.8-1.amzn2023.0.16 \
  openssl-devel-3.0.8-1.amzn2023.0.16

RUN curl -sLO https://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz \
  && tar -xzvf nginx-${NGINX_VERSION}.tar.gz \
  && curl -sLO https://github.com/openresty/headers-more-nginx-module/archive/v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && tar -xzvf v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && cd nginx-${NGINX_VERSION} \
  && ./configure --with-http_ssl_module --with-compat --add-dynamic-module=../headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION} \
  && make modules -s \
  && make install -s \
  && cd .. \
  && rm -rf nginx-${NGINX_VERSION}.tar.gz nginx-${NGINX_VERSION} v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION}

RUN ln -s /usr/local/nginx/sbin/nginx /usr/bin/nginx

RUN yum install -y -q \
  php8.3-${PHP_VERSION} \
  php8.3-bcmath-${PHP_VERSION}  \
  php8.3-cli-${PHP_VERSION}  \
  php8.3-fpm-${PHP_VERSION}  \
  php8.3-common-${PHP_VERSION}  \
  php8.3-gd-${PHP_VERSION}  \
  php8.3-mbstring-${PHP_VERSION}  \
  php8.3-mysqlnd-${PHP_VERSION}  \
  php8.3-opcache-${PHP_VERSION}  \
  php8.3-pdo-${PHP_VERSION}  \
  php8.3-soap-${PHP_VERSION} \
  php8.3-xml-${PHP_VERSION} \
  php8.3-devel-${PHP_VERSION}

RUN sed -i \
  -e 's|^memory_limit = 128M|memory_limit = 512M|' \
  -e 's|^;max_input_vars =.*|max_input_vars = 10000|' \
  /etc/php.ini

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/local/bin --filename=composer --version-${COMPOSER_VERSION} \
  && php -r "unlink('composer-setup.php');"

RUN sed -i \
  -e 's|^;clear_env = no|clear_env = no|' \
  -e 's|^listen =.*|listen = 127.0.0.1:9000|' \
  /etc/php-fpm.d/www.conf

RUN mkdir -p /var/run/php-fpm/
RUN mkdir -p /var/log/nginx
RUN mkdir -p /var/log/php-fpm

RUN curl -sLO https://xdebug.org/files/xdebug-${XDEBUG_VERSION}.tgz \
  && tar -xzvf xdebug-${XDEBUG_VERSION}.tgz \
  && cd xdebug-${XDEBUG_VERSION} \
  && phpize \
  && ./configure \
  && make \
  && make install \
  && cd .. \
  && rm -rf xdebug-${XDEBUG_VERSION}.tgz xdebug-${XDEBUG_VERSION}

COPY ./xdebug.ini /etc/php.d/50-xdebug.ini
COPY ./default.conf /usr/local/nginx/conf/nginx.conf

RUN  yum clean all -y \
  && rm -rf /var/cache/yum

EXPOSE 80

CMD ["sh", "-c", "nginx -g 'daemon off;' & php-fpm -F"]
