FROM php:5.6-apache

# install memcache depdencies
RUN apt update
RUN apt-get install -y \
	php5-xmlrpc \
	php5-memcache \
	libxml2-dev \
	memcached \
	php-pear \
	zlib1g-dev \
	build-essential \
	git

# install PHP extensions
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install xml
RUN docker-php-ext-install xmlrpc
RUN docker-php-ext-install zip
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install xdebug

# install memcache
RUN pecl config-set php_ini /usr/local/etc/php/php.ini
RUN touch /usr/local/etc/php/php.ini
RUN printf "\n" | pecl install memcache
RUN echo "extension=memcache.so" | tee /usr/local/etc/php/php.ini

# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/bin

