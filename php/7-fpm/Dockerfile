FROM php:7-fpm-alpine

LABEL maintainer="Artem Radchenkov <armit@twinscom.ru>"

### GMP

RUN apk add \
        --no-cache \
        --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ \
        libmhash-dev \
    && apk add \
        --no-cache \
        --repository http://dl-cdn.alpinelinux.org/alpine/v$(cat /etc/alpine-release | grep -E '^\d{1}\.\d+' -o)/main/ \
        re2c \
        file \
        gmp-dev \
    && ln -s /usr/include/gmp.h /usr/local/include/ \
    && docker-php-ext-configure gmp \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" gmp

### PDO_PGSQL

RUN apk add \
        --no-cache \
        postgresql-dev \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" pdo_pgsql

### INTL

RUN apk add \
        --no-cache \
        icu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" intl

### GD2

RUN apk add \
        --no-cache \
        jpeg-dev \
        libpng-dev \
        libwebp-dev \
        freetype-dev \
        oniguruma-dev \
    && docker-php-ext-configure gd \
        --with-webp \
        --with-jpeg \
        --with-freetype=/usr/include/ \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" gd

### BCMATH

RUN docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" bcmath

### SOCKETS

RUN docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" sockets

RUN docker-php-source delete
