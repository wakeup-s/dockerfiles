FROM php:7-fpm-alpine

LABEL maintainer="Artem Radchenkov <armit@twinscom.ru>"

### GMP

ARG INSTALL_GMP=false

RUN if [ ${INSTALL_GMP} = true ]; then \
    apk add \
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
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" gmp \
;fi

### PDO_PGSQL

ARG INSTALL_PDO_PGSQL=false

RUN if [ ${INSTALL_PDO_PGSQL} = true ]; then \
    apk add \
        --no-cache \
        postgresql-dev \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" pdo_pgsql \
;fi

### INTL

ARG INSTALL_INTL=false

RUN if [ ${INSTALL_INTL} = true ]; then \
    apk add \
        --no-cache \
        icu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" intl \
;fi

### GD2

ARG INSTALL_GD=false

RUN if [ ${INSTALL_GD} = true ]; then \
    apk add \
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
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" gd \
;fi

### BCMATH

ARG INSTALL_BCMATH=false

RUN if [ ${INSTALL_BCMATH} = true ]; then \
    docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" bcmath \
;fi

### SOCKETS

ARG INSTALL_SOCKETS=false

RUN if [ ${INSTALL_SOCKETS} = true ]; then \
    docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" sockets \
;fi

RUN docker-php-source delete

### FFMPEG

ARG INSTALL_FFMPEG=false

RUN if [ ${INSTALL_FFMPEG} = true ]; then \
    apk add \
        --no-cache \
        ffmpeg \
;fi

### MEDIAINFO

ARG INSTALL_MEDIAINFO=false

RUN if [ ${INSTALL_MEDIAINFO} = true ]; then \
    apk add \
        --no-cache \
        --repository http://dl-cdn.alpinelinux.org/alpine/v$(cat /etc/alpine-release | grep -E '^\d{1}\.\d+' -o)/community/ \
        mediainfo \
;fi
