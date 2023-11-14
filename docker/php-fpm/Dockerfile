FROM php:8.2-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip wget \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
COPY conf.d /usr/local/etc/php-fpm.d

WORKDIR /var/www

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

RUN groupadd -g 1000 symfony
RUN useradd -d /home/symfony -s /bin/bash -u 1000 -g 1000 symfony
RUN mkdir /home/symfony
RUN chown -R symfony:symfony /home/symfony

RUN git config --system user.email "you@example.com" \ 
    && git config --system user.name "Your Name"