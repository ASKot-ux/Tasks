FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get -y upgrade

# Install apache, PHP, and supplimentary programs. curl and lynx-cur are for debugging the container.
RUN  apt-get -y install apache2 php libapache2-mod-php php php-mbstring php-xmlrpc php-soap php-gd php-xml php-cli php-zip php-bcmath php-tokenizer php-json php-pear php-mysql
RUN apt-get -y install nano net-tools systemd wget tar make sudo composer mysql-client
RUN apt-cache search php7
#RUN touch /var/www/html/info.php
#RUN echo "<?php phpinfo(); ?>" > /var/www/html/info.php
#COPY lar /var/www/html/info.php
COPY 001-default.conf /etc/apache2/sites-available/000-default.conf
COPY 000-default.conf /etc/apache2/sites-enabled/000-default.conf
COPY config_porta /etc/apache2/ports.conf
COPY a2.conf /etc/apache2/apache2.conf
COPY p2.conf /etc/php/7.4/apache2/php.ini
COPY gulpfile.js /gulpfile.js
#RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
#RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '906a84df04cea2aa72f40b5f787e49f22d4c2f19492ac310e8cba5b96ac8b64115ac402c8cd292b8a03482574915d1a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
#RUN php composer-setup.php
#RUN php -r "unlink('composer-setup.php');"
#RUN mv composer.phar /var/www/html
WORKDIR /var/www/html
RUN git clone https://github.com/laravel/quickstart-basic quickstart
WORKDIR /var/www/html/quickstart
RUN composer install
#RUN sudo php composer.phar create-project --prefer-dist laravel/laravel projecta_name
#RUN touch /var/www/html/projecta_name/storage/logs/laravel.log
#RUN chmod 777 /var/www/html/projecta_name/storage/logs/laravel.log
#RUN chmod 777 /var/www/html/projecta_name/storage/framework/sessions/
#RUN chmod 777 /var/www/html/projecta_name/storage/framework/views
#RUN touch /var/www/html/quickstart/storage/logs/laravel.log
RUN chmod -Rv 777 /var/www/html/quickstart/storage
RUN chmod -Rv 777 /var/www/html/quickstart/vendor
RUN chmod -Rv 777 /var/www/html/quickstart/bootstrap
RUN chmod -Rv 777 /var/www/html/quickstart/vendor/laravel/framework/
#RUN chmod 777 /var/www/html/quickstart/storage/framework/sessions/
#RUN chmod 777 /var/www/html/quickstart/storage/framework/views
#RUN touch /var/www/html/quickstart/bootstrap/cache/services.php
#RUN chmod 777 /var/www/html/quickstart/bootstrap/cache
COPY dirs /etc/apache2/mods-enabled/dir.conf
COPY enveremennaia /var/www/html/quickstart/.env

EXPOSE 8080
CMD apache2ctl -D FOREGROUND

##########################################################################################

#RUN apt-get -y install git curl
#RUN curl -sS https://getcomposer.org/installer | php
#RUN mv composer.phar /usr/local/bin/composer
#RUN chmod +x /usr/local/bin/composer
#RUN composer create-project --prefer-dist laravel/laravel projecta_name
#RUN cd /projecta_name/ && php artisan serve --host=127.0.0.1 --port=80

###########################################################################################


#RUN chmod +x /var/www/html

