# Step 1: Use an official PHP image as the base
FROM php:7.3-fpm-bullseye

# Step 2: Update system time and install system dependencies
RUN  apt-get install -y tzdata && \
    ln -fs /usr/share/zoneinfo/Etc/UTC /etc/localtime && \
    dpkg-reconfigure --frontend noninteractive tzdata 

 RUN apt-get update 
 RUN apt-get install -y \
    curl \
    zip \
    unzip \
    git \
    libpq-dev \
    libzip-dev \
    libpng-dev \
    libonig-dev \
    libxml2-dev && \
    docker-php-ext-install \
    pdo_mysql \
    mbstring \
    tokenizer \
    bcmath \
    xml \
    gd \
    zip

# Step 3: Install Composer
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

# Step 4: Set the working directory
WORKDIR /var/www

# Step 5: Copy project files to the container
COPY . /var/www

# Step 6: Set permissions for storage and bootstrap/cache
# RUN chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache

# Step 7: Install Laravel dependencies
RUN composer install --no-dev --optimize-autoloader

# Step 8: Expose the default PHP-FPM port
EXPOSE 9000

# Step 9: Define the default command
CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=9000"]
