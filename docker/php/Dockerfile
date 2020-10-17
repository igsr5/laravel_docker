FROM php:7.3-fpm
COPY php.ini /usr/local/etc/php/

RUN apt-get update
RUN apt-get install -y libzip-dev
RUN apt-get install -y zlib1g-dev mariadb-client
RUN docker-php-ext-install zip pdo_mysql
RUN chown -R www-data:www-data /var/www

#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin


WORKDIR /var/www

RUN composer global require "laravel/installer"