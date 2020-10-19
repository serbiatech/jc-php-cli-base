FROM php:7.3-cli-alpine3.12

# SYS: Install required packages
RUN apk update && \
    apk --no-cache upgrade && \
    apk --no-cache add openssh autoconf bash git gcc g++ libxml2-dev make

RUN apk add librdkafka librdkafka-dev \
        --update-cache --repository http://dl-3.alpinelinux.org/alpine/edge/community

# PHP: Install php extensions
RUN pecl channel-update pecl.php.net && \
    pecl install rdkafka apcu && \
    docker-php-ext-install xml soap pcntl && \
    php-ext-enable rdkafka soap apcu
