# Use an official PHP runtime as a parent image
FROM php:8.0-fpm

# Set the working directory inside the container
WORKDIR /var/www/html/laravel-fee-management

# Copy the current directory contents into the container
COPY . /var/www/html/laravel-fee-management

# Install system dependencies, then install PHP extensions
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev zip git && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install gd pdo pdo_mysql

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install Laravel dependencies
RUN composer install

# Expose port 9000 and start PHP-FPM server
EXPOSE 9000
CMD ["php-fpm"]
