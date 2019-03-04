FROM php:7.2-apache

RUN apt-get update && apt-get install -y libpng-dev libpq-dev \
    && docker-php-ext-install gd mysqli pdo pdo_pgsql pgsql

COPY timezone.ini /usr/local/etc/php/conf.d/timezone.ini

RUN a2enmod rewrite 

RUN sed -e '/<Directory \/var\/www\/>/,/<\/Directory>/s/AllowOverride None/AllowOverride All/' -i /etc/apache2/apache2.conf

#enable directory listing menggunakan copy, 
#ganti Options -Indexes menggunakan sed masih belum berhasil
COPY custom-docker-php.conf /etc/apache2/conf-available/docker-php.conf
