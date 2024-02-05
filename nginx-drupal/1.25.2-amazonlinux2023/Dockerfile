FROM amazonlinux:2023

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Amazonlinux 2023 based image to create containers based on nginx and drupal"
LABEL version="1.25.2-amazonlinux2023"
LABEL license="Apache License 2.0"

ENV NGINX_VERSION=1.25.2
ENV HEADERS_MORE_NGINX_MODULE_VERSION=0.34
ENV PHP_VERSION=8.1.23-1.amzn2023.0.1
ENV COMPOSER_VERSION=2.6.5
ENV XDEBUG_VERSION=3.2.2
ENV NEWRELIC_PHP_AGENT_VERSION=10.13.0.2

RUN yum update -y -q \
  && yum install -y -q \
  git-2.40.1-1.amzn2023.0.1 \
  unzip-6.0-57.amzn2023.0.2 \
  tar-1.34-1.amzn2023.0.4 \
  make-4.3-5.amzn2023.0.2 \
  gcc-c++-11.4.1-2.amzn2023.0.2 \
  pcre-devel-8.44-3.amzn2023.1.0.3 \
  zlib-devel-1.2.11-33.amzn2023.0.5 \
  gcc-11.4.1-2.amzn2023.0.2 \
  autoconf-2.69-36.amzn2023.0.3

RUN curl -sLO https://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz \
  && tar -xzvf nginx-${NGINX_VERSION}.tar.gz \
  && curl -sLO https://github.com/openresty/headers-more-nginx-module/archive/v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && tar -xzvf v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz \
  && cd nginx-${NGINX_VERSION} \
  && ./configure --with-compat --add-dynamic-module=../headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION} \
  && make modules -s \
  && make install -s \
  && cd .. \
  && rm -rf nginx-${NGINX_VERSION}.tar.gz nginx-${NGINX_VERSION} v${HEADERS_MORE_NGINX_MODULE_VERSION}.tar.gz headers-more-nginx-module-${HEADERS_MORE_NGINX_MODULE_VERSION}

RUN yum install -y -q \
  php8.1-${PHP_VERSION} \
  php8.1-bcmath-${PHP_VERSION}  \
  php8.1-cli-${PHP_VERSION}  \
  php8.1-fpm-${PHP_VERSION}  \
  php8.1-common-${PHP_VERSION}  \
  php8.1-gd-${PHP_VERSION}  \
  php8.1-mbstring-${PHP_VERSION}  \
  php8.1-mysqlnd-${PHP_VERSION}  \
  php8.1-opcache-${PHP_VERSION}  \
  php8.1-pdo-${PHP_VERSION}  \
  php8.1-soap-${PHP_VERSION} \
  php8.1-xml-${PHP_VERSION} \
  php8.1-devel-${PHP_VERSION}

RUN sed -i \
  -e 's|^memory_limit = 128M|memory_limit = 512M|' \
  /etc/php.ini

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/usr/local/bin --filename=composer --version-${COMPOSER_VERSION} \
  && php -r "unlink('composer-setup.php');"

RUN sed -i \
  -e 's|^;clear_env = no|clear_env = no|' \
  -e 's|^listen =.*|listen = 127.0.0.1:9000|' \
  -e 's|^php_admin_value\[error_log\] =.*|php_admin_value[error_log] = /proc/1/fd/1|' \
  /etc/php-fpm.d/www.conf
RUN mkdir -p /var/run/php-fpm/

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

RUN curl -sLO https://download.newrelic.com/php_agent/archive/${NEWRELIC_PHP_AGENT_VERSION}/newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux.tar.gz \
  && tar -xzvf newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux.tar.gz \
  && cd newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux \
  && ln -s /etc/rc.d/init.d /etc/init.d \
  && export NR_INSTALL_USE_CP_NOT_LN=1 \
  && export NR_INSTALL_SILENT=1 \
  && ./newrelic-install install \
  && cd .. \
  && rm -rf newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux newrelic-php5-${NEWRELIC_PHP_AGENT_VERSION}-linux.tar.gz

RUN  yum clean all -y \
  && rm -rf /var/cache/yum

