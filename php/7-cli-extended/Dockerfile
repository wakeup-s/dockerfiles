FROM php:7-cli-alpine

LABEL maintainer="Artem Radchenkov <armit@twinscom.ru>"

################################################################################
# ADDITIONAL EXTENSIONS
################################################################################

RUN apk add --no-cache \
        postgresql-dev \
        icu-dev \
        freetype-dev \
        oniguruma-dev \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" pdo_pgsql intl gd sockets bcmath \
    && docker-php-source delete
