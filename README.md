# docker for magento2
---
Starting a build container with docker compose is simple:

Sample command:
- command for create your container :
```docker-compose up -d```
- command for create your container with build :
```docker-compose up -d --build```
- command for list your running container
```docker container ls```
- command for list your container all
```docker container ls -a```
- command for remove your container
```docker container rm [[container name]] or [[container id]]```
- command for access your container
```docker container exec -it [[container name]] or [[container id]] bash```
- command for get container ip
```docker container inspect```
- command for list image
```docker images ls```
- command for shutdown and remove container with compose
```docker-compose down```

---

For starting to create container plese execute this command

```docker-compose up -d```

docker will pull 4 images and create 4 containers. follow docker-compose.yml

---
**Container**
```
***container no.1 for MySQL***
version : 5.6
port: 3306
environment:
      MYSQL_ROOT_PASSWORD: magento2
      MYSQL_DATABASE: magento2
      MYSQL_USER: magento2
      MYSQL_PASSWORD: magento2
/database/mysql56/mysql/conf.d : this file for extend MySQL configurable
/database/mysql56/init : please put sql script for running script when container is starting

      
***container no.2 for redis***
version 4.0
port: 6379

***container no.3 for nginx***
version 1.12.2
port: 80
code folder : please put source code in it
/webserver/nginx/conf/default.conf : this file for extend nginx configurable


***container no.4 for php-fpm***
version php:7.0.10-fpm
port: 9000
customized.ini : this file for extend php-fpm configurable
code folder : please put source code in it
# magento2
