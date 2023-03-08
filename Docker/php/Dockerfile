FROM php:8.0-fpm

# COPY php.ini
COPY ./Docker/php/php.ini /usr/local/etc/php/php.ini

# install middleware
RUN apt-get update \
    && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libzip-dev \
        zlib1g-dev \
        unzip \
        vim \
        libyaml-dev && \
        pecl install yaml && \
        docker-php-ext-enable yaml \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
        gd \
        zip \
        pdo_mysql \
        pcntl

# Install Node.js 12
RUN apt install -y npm \
    && npm install n -g \
    && n 12

#install Composer 
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www/html

# RUN composer global require "laravel/installer"