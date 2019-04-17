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
1. Get image files of docker  
~~~
$ docker pull mysql
Using default tag: latest
latest: Pulling from library/mysql
27833a3ba0a5: Pull complete
864c283b3c4b: Pull complete
cea281b2278b: Pull complete
8f856c14f5af: Pull complete
9c4f38c23b6f: Pull complete
1b810e1751b3: Pull complete
5479aaef3d30: Pull complete
ded8fa2e1614: Pull complete
636033ba4d2e: Pull complete
902e6010661d: Pull complete
dbe44d2bf055: Pull complete
e906385f419d: Pull complete
Digest: sha256:a7cf659a764732a27963429a87eccc8457e6d4af0ee9d5140a3b56e74986eed7
Status: Downloaded newer image for mysql:latest
$ echo $?
0
$
$ docker pull wordpress
Using default tag: latest
latest: Pulling from library/wordpress
27833a3ba0a5: Already exists
2d79f6773a3c: Pull complete
f5dd9a448b82: Pull complete
95719e57e42b: Pull complete
cc75e951030f: Pull complete
78873f480bce: Pull complete
1b14116a29a2: Pull complete
887fc426d9b4: Pull complete
e8a2a7e68e47: Pull complete
44116bd4b499: Pull complete
5a7ed133cf7c: Pull complete
a0cc2e7ce3b9: Pull complete
3ea943f2a6e6: Pull complete
b7cbb4ae8469: Pull complete
f1ee59d1627e: Pull complete
480e816f1b42: Pull complete
9803a14680f4: Pull complete
a9d5149d7240: Pull complete
7a162cc00537: Pull complete
Digest: sha256:eb7fb32d7098153b586cb6c0c8c7fb3b9684c66ccff803734b0895e49210fe08
Status: Downloaded newer image for wordpress:latest
$ 
$ echo $?
0
$
~~~

2. Boot container  
~~~
$ docker run --name c-mysql -e MYSQL_ROOT_PASSWORD=passwordmysql -d mysql  
fa0a4ae326b8367aa8ab47b4fcd5d694fe4b538143c16ef55d7ca6b977bfc168  
$ docker run --name c-wordpress --link c-mysql:mysql -d -p 8080:80 wordpress  
940b8b6344c388c80a80d124190b94afe59a040080f2925e1d3b43a427604a48  
$ 
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
940b8b6344c3        wordpress           "docker-entrypoint.s…"   3 minutes ago       Up 3 minutes        0.0.0.0:8080->80/tcp   c-wordpress
fa0a4ae326b8        mysql               "docker-entrypoint.s…"   5 minutes ago       Up 5 minutes        3306/tcp, 33060/tcp    c-mysql
$
~~~

