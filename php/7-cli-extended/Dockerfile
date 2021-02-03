FROM php:7-cli-alpine

LABEL maintainer="Artem Radchenkov <armit@twinscom.ru>"

################################################################################
# ADDITIONAL EXTENSIONS
################################################################################

# For gmp-ext
RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ libmhash-dev

RUN apk add --no-cache \
        postgresql-dev \
        icu-dev \
        freetype-dev \
        oniguruma-dev \
        # for gmp-ext
        re2c \
        file \
        gmp-dev

RUN ln -s /usr/include/gmp.h /usr/local/include/ \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ \
    && docker-php-ext-configure gmp \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" pdo_pgsql intl gd sockets bcmath gmp \
    && docker-php-source delete
