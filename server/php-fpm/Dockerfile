FROM php:7.1-fpm

MAINTAINER Oleh Hrebeniuk <olehhrebeniuk@gmail.com>

# Install extensions
RUN apt-get update && apt-get install -y \
        libicu-dev \
        libpq-dev \
        curl \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev \
         --no-install-recommends \
    && docker-php-ext-install \
        intl \
        opcache \
        mcrypt \
        pdo_mysql \
        mbstring \
        tokenizer \
        zip \
    && docker-php-ext-enable \
        intl \
        zip \
        opcache \
        mcrypt \
        pdo_mysql \
        mbstring \
        tokenizer

# xdebug
RUN pecl install \
        redis \
        xdebug \
    && docker-php-ext-enable \
        redis \
        xdebug


# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN usermod -u 1000 www-data
WORKDIR /var/www/app

# Default command
CMD ["/usr/bin/supervisord"]

EXPOSE 9000
