FROM php:8.4-fpm

# Instala extensões necessárias para o Laravel
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libzip-dev \
    zip \
    unzip \
    curl \
    git

RUN docker-php-ext-install pdo_mysql gd zip

# Instala o Node.js e npm
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt-get install -y nodejs

# Instala o Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html