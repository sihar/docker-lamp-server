FROM php:5.6.38-apache

RUN apt-get update && apt-get install -y libpq-dev && docker-php-ext-install mysqli pdo pdo_pgsql pgsql

COPY timezone.ini /usr/local/etc/php/conf.d/timezone.ini

#enable directory listing menggunakan copy, 
#ganti Options -Indexes menggunakan sed masih belum berhasil
COPY custom-docker-php.conf /etc/apache2/conf-available/docker-php.conf

RUN a2enmod rewrite 