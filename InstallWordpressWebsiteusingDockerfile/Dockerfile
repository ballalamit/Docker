# MariaDB
FROM mariadb:latest
ENV MYSQL_ROOT_PASSWORD=password
ENV MYSQL_DATABASE=wordpress
ENV MYSQL_USER=wordpress
ENV MYSQL_PASSWORD=password

COPY ./database/ /var/lib/mysql

EXPOSE 3306

# Wordpress
FROM wordpress:latest
ENV WORDPRESS_DB_USER=root
ENV WORDPRESS_DB_PASSWORD=password
ENV WORDPRESS_DB_NAME=wordpress
ENV WORDPRESS_DB_HOST=mariadb

COPY ./Wordpress_Content/ /var/www/html

EXPOSE 9000
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
