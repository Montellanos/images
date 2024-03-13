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

RUN ln -s /usr/bin/php81 /usr/bin/php
RUN ln -s /usr/sbin/php-fpm81 /usr/sbin/php-fpm

RUN sed -i \
  -e 's|^max_execution_time =.*|max_execution_time = 120|' \
  -e 's|^max_input_time =.*|max_input_time = 120|' \
  -e 's|^memory_limit =.*|memory_limit = 512M|' \
  -e 's|^post_max_size =.*|post_max_size = 10M|' \
  -e 's|^upload_max_filesize =.*|upload_max_filesize = 10M|' \
  /etc/php81/php.ini

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/bin --filename=composer --version=${COMPOSER_VERSION} \
  && php -r "unlink('composer-setup.php');"

RUN sed -i \
  -e 's|^;error_log =.*|error_log = /proc/1/fd/1|' \
  -e 's|^;log_level =.*|log_level = debug|' \
  /etc/php81/php-fpm.conf

RUN sed -i \
  -e 's|^;clear_env = no|clear_env = no|' \
  -e 's|^listen =.*|listen = 127.0.0.1:9000|' \
  -e 's|^;catch_workers_output =.*|catch_workers_output = yes|' \
  -e 's|^;php_flag\[display_errors\] =.*|php_flag[display_errors] = on|' \
  -e 's|^;php_admin_value\[error_log\] =.*|php_admin_value[error_log] = /proc/1/fd/1|' \
  -e 's|^;php_admin_flag\[log_errors\] =.*|php_admin_flag[log_errors] = on|' \
  /etc/php81/php-fpm.d/www.conf
RUN mkdir -p /var/run/php-fpm/

COPY ./xdebug.ini /etc/php81/conf.d/docker-php-ext-xdebug.ini
COPY ./default.conf /etc/nginx/http.d/default.conf
COPY ./html /etc/nginx/html