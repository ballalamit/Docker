This Dockerfile uses two different images, one for MariaDB and one for WordPress. It sets the environment variables for the MariaDB container and copies the database directory to the /var/lib/mysql directory. It also exposes the port 3306.

For the WordPress container, it sets the environment variables for the database connection details, copies the Wordpress_Content directory to the /var/www/html directory, exposes port 9000 and starts the Apache server in the foreground.

You can then build the image using the Dockerfile:


docker build -t my-wordpress-image .
And then start the container with the built image


docker run --name wordpress --link mariadb:mariadb -p 9000:80 -d my-wordpress-image
Please note that this is just a basic example and you may need to adjust it according to your specific requirements.

Keep in mind that using a single file Dockerfile, it will create a single image that contains both MariaDB and WordPress, this could lead to maintainability and scalability issues, I would recommend you to use docker-compose tool to orchestrate the containers and configure the environment variables and volume mapping easily.