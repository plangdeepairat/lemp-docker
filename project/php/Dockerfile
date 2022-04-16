FROM php:8.1-fpm-alpine
RUN docker-php-ext-install mysqli
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN set -e; \
         apk add --no-cache \
                coreutils \
                freetype-dev \
                libjpeg-turbo-dev \
                libjpeg-turbo \
                libpng-dev \
                libzip-dev \
                jpeg-dev \
                icu-dev \
                zlib-dev \
                curl-dev \
                imap-dev \
                libxslt-dev libxml2-dev \
                postgresql-dev \
                libgcrypt-dev \
                oniguruma-dev

RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-configure intl
RUN docker-php-ext-configure imap

RUN set -e; docker-php-ext-install -j "$(nproc)" \
                gd soap imap bcmath mbstring curl  \
                mysqli pdo pdo_mysql \
                intl \
                zip

COPY ./laravel.ini /usr/local/etc/php/conf.d
COPY ./php.ini /usr/local/etc/php/conf.d
