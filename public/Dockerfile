# Use official PHP image as base
FROM php:8.1-fpm

# Install system dependencies for Laravel
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev libxml2-dev libssl-dev unzip git curl

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install PHP extensions required by Laravel
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql xml

# Set working directory
WORKDIR /var/www

# Copy the Laravel application to the working directory
COPY . .

# Install Composer dependencies
RUN composer install --no-interaction --prefer-dist

# Expose port 9000 and start PHP-FPM server
EXPOSE 9000
CMD ["php-fpm"]
