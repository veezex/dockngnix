FROM php:7.1-fpm-alpine3.7

WORKDIR /var/www

RUN apk update && \
    apk add freetype-dev libjpeg-turbo-dev libpng-dev && \
    docker-php-ext-install -j4 mysqli session && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install -j$(nproc) gd

#xdebug
RUN apk add --no-cache $PHPIZE_DEPS && \
	pecl install xdebug-2.6.0 && \
    docker-php-ext-enable xdebug

ADD ./xdebug.ini /usr/local/etc/php/conf.d/201-xdebug.ini

#####################################
# Copy Files:
#####################################
ADD ./php.ini /usr/local/etc/php/conf.d/php.ini

RUN chown -R www-data:www-data /var/www

USER www-data
