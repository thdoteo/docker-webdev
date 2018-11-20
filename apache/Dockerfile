FROM php:7.0-apache

RUN apt-get update -y && apt-get install -y ssmtp mailutils libpng-dev libcurl4-openssl-dev

RUN docker-php-ext-install pdo pdo_mysql mysqli gd curl zip mbstring

RUN yes | pecl install -o -f xdebug \
          && rm -rf /tmp/pear \
          && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20151012/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini \
          && echo "xdebug.remote_enable=on"  >> /usr/local/etc/php/conf.d/xdebug.ini \
          && echo "xdebug.remote_host=10.1.0.133" >> /usr/local/etc/php/conf.d/xdebug.ini \
          && echo "xdebug.remote_connect_back=On" >> /usr/local/etc/php/conf.d/xdebug.ini \
          && echo "memory_limit = 64M" > /usr/local/etc/php/conf.d/php.ini \
          && echo "xdebug.remote_autostart = 1" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN echo "hostname=localhost.localdomain" > /etc/ssmtp/ssmtp.conf
RUN echo "root=webDevDocker" >> /etc/ssmtp/ssmtp.conf
RUN echo "mailhub=maildev" >> /etc/ssmtp/ssmtp.conf
RUN echo "sendmail_path=sendmail -i -t" >> /usr/local/etc/php/conf.d/php-sendmail.ini
RUN echo "localhost localhost.localdomain" >> /etc/hosts

RUN a2enmod rewrite