FROM bitnami/php-fpm:latest
COPY ./docker/php/php-fpm.conf /usr/local/etc/php-fpm.d/www.conf
COPY . /app
VOLUME ["/app"]

