FROM php:7.2.1-fpm 
RUN groupadd www && useradd -g www -s /sbin/nologin www
COPY php.ini /usr/local/etc/php/php.ini
COPY php-fpm.conf /usr/local/etc/php-fpm.conf
COPY php-fpm.d/www.conf /usr/local/etc/php-fpm.d/www.conf
COPY redis-5.1.0.tgz /home/redis-5.1.0.tgz
COPY memcached-3.1.4.tgz /home/memcached-3.1.4.tgz
#COPY xdebug-2.6.0.tgz /home/xdebug-2.6.0.tgz
RUN apt-get update && apt-get install -y \
     libfreetype6-dev \
     libjpeg62-turbo-dev \
     libmcrypt-dev \
     libpng-dev \
     libz-dev libmemcached-dev \
     && docker-php-ext-install gd \
     && docker-php-ext-install pdo_mysql \
     && pecl install redis-5.1.0.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini \
     && pecl install memcached-3.1.4.tgz && echo "extension=memcached.so" > /usr/local/etc/php/conf.d/memcached.ini \
     && rm -r /home/memcached-3.1.4.tgz \
     #&& tar -xf /home/xdebug-2.6.0.tgz \
     #&& rm -rf /home/xdebug-2.6.0.tgz \
     && mkdir -p /usr/src/php/ext \
     #&& mv xdebug-2.6.0 /usr/src/php/ext/xdebug \
     #&& docker-php-ext-install xdebug \
     && rm -rf /home/redis-3.1.6.tgz
 
  
RUN docker-php-ext-install bcmath
ADD composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer
VOLUME /var/www/

