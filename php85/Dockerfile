FROM php:8.5-apache

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libicu-dev \
    libonig-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    libzip-dev \
    zlib1g-dev \
    unzip \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Configure GD
RUN docker-php-ext-configure gd \
    --with-freetype \
    --with-jpeg

# Install PHP extensions (CodeIgniter 4)
RUN docker-php-ext-install -j$(nproc) \
    intl \
    mbstring \
    mysqli \
    pdo \
    pdo_mysql \
    gd \
    zip \
    bcmath \
    exif

# Enable Apache rewrite
RUN a2enmod rewrite

# ✅ Install Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

