FROM amazonlinux:2

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Amazonlinux 2 based image to create containers based on nginx and drupal"
LABEL version="1.21.0-amazonlinux2"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.21.0
ENV HEADERS_MORE_NGINX_MODULE_VERSION=0.33

ENV PHP_VERSION=7.4.33-1.amzn2
ENV COMPOSER_VERSION=2.5.7
ENV XDEBUG_VERSION=3.0.4
ENV NEWRELIC_PHP_AGENT_VERSION=10.11.0.3

RUN yum install -y -q deltarpm-3.6-3.amzn2.0.2
RUN sed -i -e '$a deltarpm=0' /etc/yum.conf

RUN yum update -y -q \
  && yum install -y -q \
  git-2.40.1-1.amzn2.0.1 \
  unzip-6.0-57.amzn2.0.1 \
  tar-1.26-35.amzn2.0.2 \
  make-3.82-24.amzn2 \
  gcc-c++-7.3.1-17.amzn2 \
  pcre-devel-8.32-17.amzn2.0.3 \
  zlib-devel-1.2.7-19.amzn2.0.2 \
  gcc-7.3.1-15.amzn2 \
  autoconf-2.69-11.amzn2 \
  php-devel-5.4.16-46.amzn2.0.2

RUN curl -sLO http://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz \
  && tar -xzvf nginx-${NGINX_VERSION}.tar.gz \
  && curl -sLO https://github.com/openresty/headers-more-nginx-module/archive/v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && tar -xzvf v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && cd nginx-${NGINX_VERSION} \
  && ./configure --with-compat --add-dynamic-module=../headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION} \
  && make modules -s \
  && make install -s \
  && cd .. \
  && rm -rf nginx-${NGINX_VERSION}.tar.gz nginx-${NGINX_VERSION} v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION}

RUN amazon-linux-extras enable php7.4

RUN yum install -y -q \
  php-${PHP_VERSION} \
  php-bcmath-${PHP_VERSION}  \
  php-cli-${PHP_VERSION}  \
  php-fpm-${PHP_VERSION}  \
  php-common-${PHP_VERSION}  \
  php-gd-${PHP_VERSION}  \
  php-json-${PHP_VERSION}  \
  php-mbstring-${PHP_VERSION}  \
  php-mysqlnd-${PHP_VERSION}  \
  php-opcache-${PHP_VERSION}  \
  php-pdo-${PHP_VERSION}  \
  php-pecl-igbinary-3.1.2-1.amzn2 \
  php-pecl-redis-5.2.1-1.amzn2 \
  php-soap-${PHP_VERSION} \
  php-xml-${PHP_VERSION}

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/local/bin --filename=composer --version-${COMPOSER_VERSION} \
  && php -r "unlink('composer-setup.php');"

RUN sed -i \
  -e 's|^listen =.*|listen = 127.0.0.1:9000|' \
  -e 's|^php_admin_value\[error_log\] =.*|php_admin_value[error_log] = /proc/1/fd/1|' \
  /etc/php-fpm.d/www.conf

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

RUN rpm -Uvh https://yum.newrelic.com/pub/newrelic/el5/x86_64/newrelic-repo-5-3.noarch.rpm \
  && yum install -y newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}

RUN  yum clean all -y \
  && rm -rf /var/cache/yum

RUN chmod -R 755 /var/www/html
