FROM alpine:3.19.1

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx and drupal"
LABEL version="1.24.0-alpine3.19"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.24.0-r15
ENV PHP_VERSION=8.1.27-r0
ENV COMPOSER_VERSION=2.7.0

RUN apk update && apk add --no-cache \
  nginx=${NGINX_VERSION} \
  nginx-mod-http-headers-more=${NGINX_VERSION} \
  git=2.43.0-r0 \
  unzip=6.0-r14 \
  php81=${PHP_VERSION} \
  php81-bcmath=${PHP_VERSION} \
  php81-fpm=${PHP_VERSION} \
  php81-common=${PHP_VERSION} \
  php81-gd=${PHP_VERSION} \
  php81-mbstring=${PHP_VERSION} \
  php81-mysqlnd=${PHP_VERSION} \
  php81-opcache=${PHP_VERSION} \
  php81-pdo=${PHP_VERSION} \
  php81-pecl-igbinary=3.2.15-r0 \
  php81-pecl-redis=6.0.2-r0 \
  php81-soap=${PHP_VERSION} \
  php81-xml=${PHP_VERSION} \
  php81-simplexml=${PHP_VERSION} \
  php81-tokenizer=${PHP_VERSION} \
  php81-dom=${PHP_VERSION} \
  php81-ctype=${PHP_VERSION} \
  php81-iconv=${PHP_VERSION} \
  php81-curl=${PHP_VERSION} \
  php81-xmlreader=${PHP_VERSION} \
  php81-xmlwriter=${PHP_VERSION} \
  php81-pdo_mysql=${PHP_VERSION} \
  php81-phar=${PHP_VERSION} \
  php81-pear=${PHP_VERSION} \
  php81-pecl-xdebug=3.3.1-r0 \
  php81-zip=${PHP_VERSION} 


RUN sed -i \
  -e 's|^memory_limit = 128M|memory_limit = 512M|' \
  /etc/php81/php.ini

RUN php81 -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php81 composer-setup.php --install-dir=/usr/bin --filename=composer --version=${COMPOSER_VERSION} \
  && php81 -r "unlink('composer-setup.php');"

RUN sed -i \
  -e 's|^;clear_env = no|clear_env = no|' \
  -e 's|^listen =.*|listen = 127.0.0.1:9000|' \
  -e 's|^php_admin_value\[error_log\] =.*|php_admin_value[error_log] = /proc/1/fd/1|' \
  /etc/php81/php-fpm.d/www.conf
RUN mkdir -p /var/run/php-fpm/

COPY ./xdebug.ini /etc/php81/conf.d/docker-php-ext-xdebug.ini

