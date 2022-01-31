ARG PHP_VERSION=7.1
FROM composer:latest AS composer
FROM php:${PHP_VERSION}-fpm
COPY --from=composer /usr/bin/composer /usr/bin/composer

LABEL author.name = "Evgeniy Terin"
LABEL author.email = "web@derin.ru"

RUN apt-get update && apt-get install -y wget unzip libzip-dev

# GD extension
#RUN apt-get update && apt-get install -y \
#		libfreetype6-dev \
#		libjpeg62-turbo-dev \
#		libpng-dev \
#	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#	&& docker-php-ext-install -j$(nproc) gd

# PECL extensions: xdebug
RUN pecl install xdebug-3.1.2 && docker-php-ext-enable xdebug

# Standart PHP extensions
#RUN docker-php-ext-install bcmath
#RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN docker-php-ext-install zip
#RUN docker-php-ext-install pdo_mysql && docker-php-ext-enable pdo_mysql
#RUN docker-php-ext-install pcntl

# Postgres PHP extensions
RUN apt-get update && \
    apt-get install -y libpq-dev && \
    docker-php-ext-install pdo pdo_pgsql pgsql


ADD "my-php.ini" "/usr/local/etc/php/conf.d/my-php.ini"

ARG USER_ID=1000
ARG GROUP_ID=1000
RUN usermod -u ${USER_ID} www-data && groupmod -g ${GROUP_ID} www-data
#RUN chown -R www-data:www-data /var/www/

#ARG TIMEZONE
#ENV TZ=${TIMEZONE}

WORKDIR /var/www
