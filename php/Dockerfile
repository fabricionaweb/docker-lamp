# Official
FROM php:5.6-apache

COPY php.ini /usr/local/etc/php/

# Libs for compile modules
RUN apt-get update && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev libssl-dev zlib1g-dev libicu-dev 
RUN apt-get install -y libmagickwand-dev --no-install-recommends

# Install modules
RUN docker-php-ext-install pdo_mysql mysqli mbstring gd iconv mcrypt intl

# Pecl modules
RUN pecl install mongo imagick && docker-php-ext-enable mongo imagick 

# Clear apt
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

# Enable mod_rewrite
RUN a2enmod rewrite