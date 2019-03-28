FROM php:7.2-apache

#menambah extension gd dan imagick
RUN apt-get update && apt-get install -y libmagickwand-dev --no-install-recommends libpng-dev libpq-dev \
 && docker-php-ext-install gd mysqli pdo_mysql pdo_pgsql pgsql \
 && pecl install imagick \
 && docker-php-ext-enable imagick \
 && rm -r /var/lib/apt/lists/*

COPY timezone.ini /usr/local/etc/php/conf.d/timezone.ini

RUN sed -e '/<Directory \/var\/www\/>/,/<\/Directory>/s/AllowOverride None/AllowOverride All/' -i /etc/apache2/apache2.conf

#enable directory listing menggunakan copy, 
#ganti Options -Indexes menggunakan sed masih belum berhasil
COPY custom-docker-php.conf /etc/apache2/conf-available/docker-php.conf

#enable mod_rewrite in apache
RUN a2enmod rewrite 