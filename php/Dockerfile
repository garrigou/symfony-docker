FROM php:8.0-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

WORKDIR /var/www

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN echo 'deb [trusted=yes] https://repo.symfony.com/apt/ /' | tee /etc/apt/sources.list.d/symfony-cli.list
RUN apt update
RUN apt install symfony-cli


RUN groupadd -g 1000 symfony
RUN useradd -d /home/symfony -s /bin/bash -u 1000 -g 1000 symfony
RUN mkdir /home/symfony
RUN chown -R symfony:symfony /home/symfony

RUN git config --system user.email "you@example.com" \ 
    && git config --system user.name "Your Name"