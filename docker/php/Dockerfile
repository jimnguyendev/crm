FROM php:8.1-fpm

WORKDIR /var/www/vhost/

# Set new UID for user www-data
RUN usermod -u 1000 www-data

# Install dependencies
RUN apt-get clean && apt-get update && apt-get upgrade -y && apt-get install -y \
    git \
    libcurl4-openssl-dev \
    libonig-dev \
    libpng-dev \
    libssl-dev \
    libicu-dev \
    libxml2-dev \
    libzip-dev \
    unzip \
    wget \
    zip \
    tzdata

RUN docker-php-ext-configure intl
# PHP Extensions
RUN docker-php-ext-install \
    bcmath \
    exif \
    gd \
    mysqli \
    opcache \
    pdo_mysql \
    pcntl \
    xml \
    zip \
    intl

# Install PECL extensions
RUN pecl install redis \
    && docker-php-ext-enable redis

# Install Composer from Official Docker Image
# https://hub.docker.com/_/composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
