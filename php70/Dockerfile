FROM php:7.0.32-apache

RUN apt-get update && apt-get install -y libpq-dev && docker-php-ext-install mysqli pdo pdo_pgsql pgsql

COPY timezone.ini /usr/local/etc/php/conf.d/timezone.ini
