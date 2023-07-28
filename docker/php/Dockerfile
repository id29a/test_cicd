FROM php:8.1.11-fpm

ADD ./php.ini /opt/docker/etc/php/php.ini

RUN rm /etc/apt/preferences.d/no-debian-php && apt-get update && apt-get install -y libxml2-dev php-soap && docker-php-ext-install soap

RUN docker-php-ext-install pdo mysqli pdo_mysql

RUN apt-get update && apt-get install -y libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev \
    optipng jpegoptim pngtools \
    ghostscript \
    webp \
    gifsicle \
    npm \
    && npm -g install svgo \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
    
RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
    
RUN docker-php-ext-install gd

RUN groupmod -g 999 www-data

WORKDIR "/var/www/bitrix"
