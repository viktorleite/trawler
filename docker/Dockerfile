FROM php:8.3-fpm

LABEL maintainer="Vitor L. Santos <vitorleit3@gmail.com>"
LABEL company="Hurezo"

ARG user=trawler
ARG uid=1000
WORKDIR /var/www/html

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libzip-dev \
    libpng-dev \
    libpq-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
   supervisor

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
# RUN docker-php-ext-install pdo_mysql pdo msqli pdo_pgsql xml mbstring exif pcntl bcmath gd sockets
RUN docker-php-ext-install pdo \ 
    pdo_mysql \
    session \
    xml \
    mbstring \
    exif \
    pcntl \
    bcmath \
    gd \
    sockets \
    fileinfo \
    zip \
    simplexml \
    intl \
    opcache \
    gd \
    exif \
    bcmath 
# Install Swoole
RUN pecl install swoole
RUN docker-php-ext-enable swoole

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

COPY supervisord.conf /etc/supervisord.conf
COPY ./php.ini /usr/local/etc/php/conf.d/custom.ini

# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u $uid -d /home/$user $user
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/$user

# Install redis
RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis



EXPOSE 8000

CMD [ "/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]
