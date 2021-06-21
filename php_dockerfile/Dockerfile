FROM php:7.4-fpm

LABEL maintainer="fangxh2013 <fangxh2013@gmail.com>"
LABEL version="2.0"
LABEL description="php7.4-fpm + nginx + mysqli + redis"

RUN set -ex; \
	apt-get update; \
	apt-get install -y --no-install-recommends \
        iputils-ping \
		imagemagick \
		less \
		mariadb-client \
		msmtp \
		libc-client-dev \
		libfreetype6-dev \
		libjpeg-dev \
		libjpeg62-turbo-dev \
		libkrb5-dev \
		libmagickwand-dev \
		libmcrypt-dev \
		libicu-dev \
		libmemcached-dev \
		libxml2-dev \
		libpng-dev \
		libzip-dev \
		libssl-dev \
		unzip \
		vim \
		zip

RUN pecl install imagick; \
	pecl install mcrypt-1.0.3; \
	pecl install redis; \
	pecl install swoole; \
	docker-php-ext-configure gd --with-freetype --with-jpeg; \
	docker-php-ext-configure zip; \
	docker-php-ext-install gd; \
	PHP_OPENSSL=yes docker-php-ext-configure imap --with-kerberos --with-imap-ssl; \
	docker-php-ext-install imap; \
	docker-php-ext-install mysqli; \
	docker-php-ext-install pdo_mysql; \
	docker-php-ext-install opcache; \
	docker-php-ext-install soap; \
	docker-php-ext-install intl; \
	docker-php-ext-install zip; \
	docker-php-ext-install exif; \
	docker-php-ext-enable mysqli imagick mcrypt redis swoole; \
	docker-php-ext-install bcmath; \
	apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false; \
	rm -rf /var/lib/apt/lists/*;