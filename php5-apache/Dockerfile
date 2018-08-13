FROM php:5.5-apache

MAINTAINER Damian Szymczuk (dszymczuk)

# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive


RUN apt-get update && \
apt-get install -y mcrypt libmcrypt-dev imagemagick libpng-dev

RUN docker-php-ext-install mbstring mcrypt mysql mysqli pdo pdo_mysql zip gd
RUN docker-php-ext-enable mbstring mcrypt mysql mysqli pdo pdo_mysql zip gd

RUN cd /tmp && curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer
RUN apt-get remove -y && \
apt-get -y autoremove && \
apt-get clean && \
rm -rf /var/lib/apt/lists/*

RUN echo "memory_limit=512M" > /usr/local/etc/php/conf.d/memory-limit.ini

RUN a2enmod rewrite

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
