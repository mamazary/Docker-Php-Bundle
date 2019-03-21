# Extend from php7.0-apache official image ( debian-stretch )
FROM php:7.0-apache

# Update the os feature & patch
RUN apt-get update

# Install required app & extention
RUN apt-get install -y libjpeg62-turbo-dev libpng-dev libfreetype6-dev \
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-install -j$(nproc) gd \
&& docker-php-ext-install pdo_mysql

# Install php extension
RUN apt-get install -y libmcrypt-dev

# enable mod-rewrite module
RUN a2enmod rewrite

# Expose port & CMD will inherit from official php image
