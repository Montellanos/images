ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM alpine:3.19.4

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx and drupal"
LABEL version="1.24.0-alpine3.19"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.24.0-r16
ENV PHP_VERSION=8.2.26-r0
ENV COMPOSER_VERSION=2.8.4

RUN apk update && apk add --no-cache \
  nginx=${NGINX_VERSION} \
  nginx-mod-http-headers-more=${NGINX_VERSION} \
  git=2.43.6-r0 \
  unzip=6.0-r14 \
  jq=1.7.1-r0 \
  libcrypto3=3.1.7-r1 \
  libssl3=3.1.7-r1 \
  libcurl=8.11.1-r0 \
  busybox=1.36.1-r19 \
  php82=${PHP_VERSION} \
  php82-bcmath=${PHP_VERSION} \
  php82-fpm=${PHP_VERSION} \
  php82-common=${PHP_VERSION} \
  php82-gd=${PHP_VERSION} \
  php82-mbstring=${PHP_VERSION} \
  php82-mysqlnd=${PHP_VERSION} \
  php82-opcache=${PHP_VERSION} \
  php82-pdo=${PHP_VERSION} \
  php82-pecl-igbinary=3.2.15-r0 \
  php82-pecl-redis=6.0.2-r0 \
  php82-soap=${PHP_VERSION} \
  php82-xml=${PHP_VERSION} \
  php82-simplexml=${PHP_VERSION} \
  php82-tokenizer=${PHP_VERSION} \
  php82-dom=${PHP_VERSION} \
  php82-ctype=${PHP_VERSION} \
  php82-iconv=${PHP_VERSION} \
  php82-curl=${PHP_VERSION} \
  php82-xmlreader=${PHP_VERSION} \
  php82-xmlwriter=${PHP_VERSION} \
  php82-pdo_mysql=${PHP_VERSION} \
  php82-phar=${PHP_VERSION} \
  php82-pear=${PHP_VERSION} \
  php82-pecl-xdebug=3.3.2-r0 \
  php82-zip=${PHP_VERSION} \
  php82-mysqli=${PHP_VERSION}

RUN ln -s /usr/sbin/php-fpm82 /usr/sbin/php-fpm

RUN sed -i \
  -e 's|^memory_limit =.*|memory_limit = 512M|' \
  -e 's|^;max_input_vars =.*|max_input_vars = 10000|' \
  /etc/php82/php.ini

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/bin --filename=composer --version=${COMPOSER_VERSION} \
  && php -r "unlink('composer-setup.php');"

RUN sed -i \
  -e 's|^user =.*|user = nginx|' \
  -e 's|^group =.*|group = nginx|' \
  -e 's|^listen =.*|listen = 127.0.0.1:9000|' \
  -e 's|^;listen.owner =.*|listen.owner = nginx|' \
  -e 's|^;listen.group =.*|listen.group = nginx|' \
  -e 's|^pm =.*|pm = ondemand|' \
  -e 's|^pm.max_children =.*|pm.max_children = 150|' \
  -e 's|^;pm.process_idle_timeout =.*|pm.process_idle_timeout = 10s|' \
  -e 's|^;pm.max_requests =.*|pm.max_requests = 500|' \
  -e 's|^;access.log =.*|access.log = /var/log/php82/php82.access.log|' \
  -e 's|^;slowlog =.*|slowlog = /var/log/php82/php82-$pool.slow.log|' \
  -e 's|^;request_slowlog_timeout =.*|request_slowlog_timeout = 60s|' \
  -e 's|^;request_terminate_timeout =.*|request_terminate_timeout = 90s|' \
  -e 's|^;catch_workers_output =.*|catch_workers_output = yes|' \
  -e 's|^;clear_env =.*|clear_env = no|' \
  -e 's|^;php_admin_value\[memory_limit\] =.*|php_admin_value[memory_limit] = 512M|' \
  -e 's|^;php_admin_value\[error_log\] =.*|php_admin_value[error_log] = /var/log/php82/php82-error.log|' \
  /etc/php82/php-fpm.d/www.conf

RUN mkdir -p /var/run/php-fpm/
RUN mkdir -p /var/log/php-fpm82
RUN mkdir -p /var/log/nginx

COPY ./xdebug.ini /etc/php82/conf.d/docker-php-ext-xdebug.ini
COPY ./default.conf /etc/nginx/http.d/default.conf
COPY ./html /etc/nginx/html

EXPOSE 80

CMD ["sh", "-c", "nginx -g 'daemon off;' & php-fpm -F"]
