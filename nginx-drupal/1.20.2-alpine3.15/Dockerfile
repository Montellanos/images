FROM alpine:3.15.9

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on nginx and drupal"
LABEL version="1.20.2-alpine3.15"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.20.2-r1
ENV PHP_VERSION=7.4.33-r1
ENV COMPOSER_VERSION=2.5.7
ENV NEWRELIC_PHP_AGENT_VERSION=9.16.0.295

RUN apk update && apk add --no-cache \
  openssl=1.1.1u-r1 \
  nginx=${NGINX_VERSION} \
  nginx-mod-http-headers-more=${NGINX_VERSION} \
  git=2.34.8-r0 \
  unzip=6.0-r9 \
  php7=${PHP_VERSION} \
  php7-bcmath=${PHP_VERSION} \
  php7-cli \
  php7-fpm=${PHP_VERSION} \
  php7-common=${PHP_VERSION} \
  php7-gd=${PHP_VERSION} \
  php7-json=${PHP_VERSION} \
  php7-mbstring=${PHP_VERSION} \
  php7-mysqlnd=${PHP_VERSION} \
  php7-opcache=${PHP_VERSION} \
  php7-pdo=${PHP_VERSION} \
  php7-pecl-igbinary=3.2.6-r0 \
  php7-pecl-redis=5.3.6-r0 \
  php7-soap=${PHP_VERSION} \
  php7-xml=${PHP_VERSION} \
  php7-simplexml=${PHP_VERSION} \
  php7-tokenizer=${PHP_VERSION} \
  php7-dom=${PHP_VERSION} \
  php7-ctype=${PHP_VERSION} \
  php7-iconv=${PHP_VERSION} \
  php7-curl=${PHP_VERSION} \
  php7-xmlreader=${PHP_VERSION} \
  php7-xmlwriter=${PHP_VERSION} \
  php7-pdo_mysql=${PHP_VERSION} \
  php7-phar=${PHP_VERSION} \
  php7-pear=${PHP_VERSION} \
  php7-pecl-xdebug=3.1.4-r0 \
  php7-zip=${PHP_VERSION} 

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/bin --filename=composer --version=${COMPOSER_VERSION} \
  && php -r "unlink('composer-setup.php');"

COPY ./xdebug.ini /etc/php7/conf.d/docker-php-ext-xdebug.ini

RUN wget --no-verbose https://download.newrelic.com/php_agent/archive/${NEWRELIC_PHP_AGENT_VERSION}/newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux-musl.tar.gz \
  && tar -xvf newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux-musl.tar.gz \
  && NR_INSTALL_USE_CP_NOT_LN=1 NR_INSTALL_SILENT=1 ./newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux-musl/newrelic-install install\
  && rm -rf newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux-musl.tar.gz \
  && rm -rf newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux-musl

RUN mkdir /var/www/html \
  && chmod -R 755 /var/www/html
