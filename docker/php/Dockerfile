FROM php:8.1.5-fpm-alpine
COPY ./docker/php/php-fpm.conf /usr/local/etc/php-fpm.d/www.conf
COPY . /app
VOLUME ["/app"]

