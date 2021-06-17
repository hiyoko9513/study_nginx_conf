FROM php:7.4-fpm
WORKDIR /var/www/html

RUN cd /usr/bin && curl -s http://getcomposer.org/installer \n\
    | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
    && apt-get install -y \
    git \
    zip \
    unzip \
    vim

RUN apt-get update \
    && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo_mysql pdo_pgsql mysqli

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

#COPY ./php/php.ini /usr/local/etc/php/

RUN curl -sSLO https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 \
    && chmod +x mhsendmail_linux_amd64 \
    && mv mhsendmail_linux_amd64 /usr/local/bin/mhsendmail
