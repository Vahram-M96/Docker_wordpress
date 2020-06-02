# Wordpress_docker   
## Description 
This project will help you to setup Wordpress with docker containers.We will use a three containers: nginx, PHP, mysql. PHP container we will create using Docker file in order to be sure that all necessary packages are included in our PHP container.For this project we use docker compose to make this process more automated.  
Also, it can help beginner programmers create a test environment for their projects.

## Components
 1. docker-compose.yml file:   
    * this file is used to define all necessary containers and their parameters for this project  
2. The "nginx" directory:
   * This directory is used to store the config file for nginx. It mounted to  nginx container /etc/nginx/conf.d/ directory.
3. The "mysql " directory:
    * it's used as the storage for mysql,and mounted to /var/lib/mysql directory in mysql container.
4. Dockerfile  
     * This dockerfile is used in the PHP container creation process.
5. The "php_new_conf" directory:
     * This directory contains all PHP related files (config files). All changes in this directory will affect to PHP container work.This directory mounted under /etc/php/7.3 directory of PHP container.
6. The "wpcpnf" directory:
     * this directory keep the wp-config.php file, whic is used to connect wordpress to database   

> In this project  the "www" volume is used to share WordPress between "nginx" and "php7. 3-fpm" containers. It is mounted to the same directory on "nginx" and "PHP" container's (/var/www/html/)
## Usage:
>#### Pre requirepmants 
>You should have pre instolled Docker ,Docker-compose   
>If you dont have this components pleas check links below.  
>[Docker  installation](https://docs.docker.com/get-docker/)  
>[Docker-compose installation](https://docs.docker.com/compose/install/)

1. Get all files and directories to your project's working directory
2. Make changes in docker-compose.yml file:
     * Change user, password and database configurations in "**_environment:_**" dictionary for services, mysql and Wordpress (as you need for your project).
3. Make changes in nginx. 
     * Conf file which is located in "nginx" directory:
change the dictionary "**_server_name_**" (it should be any DNS name which you want to use to reach your Wordpress site).
4. Run Application 
    * docker-compose up -d 
5. Go to your browser. Browse a domain name of your project on port: 80 (If you don't have an entry in your docker host's /etc/hosts file for the domain name that you use for your project you can browse your localhost on same port: 8080. Also keep in mind that the port: 8080 is mentioned in docker-compose.yml file and you can change it. For that you need to change the value of "**_ports:_**" parameters for nginx service in docker-compose.yml file)
