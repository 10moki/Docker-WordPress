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
$

~~~
