# Docker-WordPress

## Environment
* OS  
 macOS 10.12.6

## Procedure  
### 1. Install Docker
1. Download  
Download *Docker CE for Mac* from the following .  
https://hub.docker.com/editions/community/docker-ce-desktop-mac  
!! if you don't have an account of docker , you have to create it .  

2. Install  
Double click Docker Image and follow the instruction .  

3. Start Docker App  
Start Docker App and Log in Docker account followeing the instruction .  
Then open terminal and type in the following commond to confirm using it . 
~~~
$ docker info
$ docker ps
~~~

### 2. Build WordPress Enviroment  
1. Create a docker-compose.yml  
Reference : https://docs.docker.com/compose/wordpress/  
~~~
$ cd my_wordpress
$ touch docker-compose.yml
$ vi docker-compose.yml
-------------------------------------
version: '3.3'

services:
   db:
     container_name: c-mysql
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
       - ./db_data:/docker-entrypoint-initdb.d
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     container_name: c-wordpress
     depends_on:
       - db
     image: wordpress:latest
     volumes:
       - ./www:/var/www/html
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
-------------------------------------
~~~

2. Boot container  
~~~
$ docker-compose up -d
Creating network "my_wordpress_default" with the default driver
Creating c-mysql ... done
Creating c-wordpress ... done
$ 
~~~
if you want to down container , you can use the following command  
$ docker-compose down  
$ docker-compose stop  

3. Access Wordpress on browser  
Access localhost on browser 
http://localhost:8000/


