FROM debian:buster

RUN apt-get update
RUN apt-get -y install nginx

RUN apt-get -y install mariadb-server

RUN apt-get -y install php7.3 php-mysql php-fpm php-pdo php-gd php-cli php-mbstring

RUN apt-get -y install wget
# RUN openssl req -x509 -nodes -days 365 -subj "/C=RU/ST=RUSSIA/L=kazan/O=innoaca/OU=42kazan/CN=forhjy" -newkey rsa:2048 -keyout /etc/ssl/nginx-selfsigned.key -out /etc/ssl/nginx-selfsigned.crt

WORKDIR /var/www
RUN wget https://wordpress.org/latest.tar.gz
RUN tar -xvzf latest.tar.gz && rm -rf latest.tar.gz

COPY ./wordpress/wp-config.php /var/www/wordpress
COPY ./nginx/default /etc/nginx/sites-available
#RUN ln -s /etc/nginx/sites-available/wp.conf /etc/nginx/sites-enabled
RUN chown -R www-data:www-data *
RUN chmod -R 755 /var/www/*
COPY init.sh /home


CMD bash /home/init.sh

EXPOSE 443
