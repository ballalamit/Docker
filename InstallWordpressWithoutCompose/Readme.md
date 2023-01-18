sudo docker run -e MYSQL_ROOT_PASSWORD=<password> -e MYSQL_DATABASE=wordpress --name wordpressdb -v "$PWD/database":/var/lib/mysql -d mariadb:latest

This command is using Docker to run a MariaDB container with the following options:

-e MYSQL_ROOT_PASSWORD=<password>: This sets the root password for the MariaDB instance to the value specified in place of <password>.
-e MYSQL_DATABASE=wordpress: This creates a new database in the MariaDB instance with the name 'wordpress'
--name wordpressdb: This sets the name of the container as 'wordpressdb'
-v "$PWD/database":/var/lib/mysql: This creates a volume that maps the host's $PWD/database directory to the /var/lib/mysql directory inside the container, so any data that is written to the /var/lib/mysql directory inside the container will be persisted in the host's $PWD/database directory.
-d: This runs the container in detached mode, allowing it to run in the background.
mariadb:latest: This specifies the image to use for the container. In this case, it is the latest version of the official MariaDB image.
In summary, this command creates a new container with the name 'wordpressdb' running a MariaDB instance with the root password set to the one given, creating a new database called 'wordpress' and mapping the host's '$PWD/database' directory to the '/var/lib/mysql' directory inside the container. This will allow to persist the data and run the container in detached mode.


docker run -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=password --name wordpress --link wordpressdb:mysql -p 9000:80 -v "$PWD/Wordpress_Content":/var/www/html -d wordpress


This command is using Docker to run a Wordpress container with the following options:

-e WORDPRESS_DB_USER=root: This sets the database user for Wordpress to 'root'
-e WORDPRESS_DB_PASSWORD=password: This sets the database password for the user 'root' to 'password'
--name wordpress: This sets the name of the container as 'wordpress'
--link wordpressdb:mysql: This links the 'wordpressdb' container to the 'wordpress' container, allowing the 'wordpress' container to connect to the database in the 'wordpressdb' container using the hostname 'mysql'
-p 9000:80: This maps port 9000 on the host to port 80 on the container, allowing connections to the Wordpress instance on the host via port 9000
-v "$PWD/Wordpress_Content":/var/www/html: This creates a volume that maps the host's $PWD/WordPress_Content directory to the /var/www/html directory inside the container, so any data that is written to the /var/www/html directory inside the container will be persisted in the host's $PWD/Wordpress_Content directory.
-d: This runs the container in detached mode, allowing it to run in the background.
wordpress: This specifies the image to use for the container. In this case, it is the official Wordpress image
In summary, this command creates a new container with the name 'wordpress' running a Wordpress instance with the database user and password set to 'root' and 'password' respectively, linking it with the 'wordpressdb' container, mapping the host's port 9000 to container's port 80, mapping the host's '$PWD/WordPress_Content' directory to the '/var/www/html' directory inside the container and run the container in detached mode.