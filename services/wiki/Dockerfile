# MediaWiki

# Use php from Aliyun's registry
FROM w6wy7kfr.mirror.aliyuncs.com/library/php:7.0.12-apache

MAINTAINER Da Wei, xichuanglian@gmail.com

ADD sources.list /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y git diffutils

RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libicu-dev \
    && docker-php-ext-install -j$(nproc) mcrypt intl\
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN pecl install apcu && docker-php-ext-enable apcu

RUN docker-php-ext-install mysqli

#ADD www.conf /usr/local/etc/php-fpm.d/www.conf
