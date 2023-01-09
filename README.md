[![Build](https://github.com/jkaninda/nginx-fpm/actions/workflows/build.yml/badge.svg)](https://github.com/jkaninda/nginx-fpm/actions/workflows/build.yml)
![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/jkaninda/nginx-fpm?style=flat-square)
![Docker Pulls](https://img.shields.io/docker/pulls/jkaninda/nginx-fpm?style=flat-square)

# Nginx Web server for PHP FPM


> 🐳 Nginx Web server for PHP FPM.

- [Docker Hub](https://hub.docker.com/r/jkaninda/nginx-fpm)
- [Github](https://github.com/jkaninda/nginx-fpm)

## Simple docker-compose usage:

```yml
version: '3'
services:
    nginx-server:
     image: jkaninda/nginx-fpm:alpine
     container_name: nginx-server
     restart: unless-stopped
     ports:
      - 80:80
     volumes:
      - ./:/var/www/html
     environment:
       - DOCUMENT_ROOT=/var/www/html
       - CLIENT_MAX_BODY_SIZE=20M
       - PHP_FPM_HOST=php-fpm-host:9000 
     networks:
      - default

```
## Advanced Nginx-fpm with PHP FPM:
### docker-compose.yml

```yml
version: '3'
services:
    php-fpm:
        image: jkaninda/laravel-php-fpm:8.1 
        container_name: php-fpm
        restart: unless-stopped 
        pull_policy: if_not_present
        volumes:
        #Project root
            - ./:/var/www/html
        ports:
            - 9000
        networks:
            - default #if you're using networks between containers
    #Nginx server
    nginx-server:
     image: jkaninda/nginx-fpm:alpine
     container_name: nginx-server
     restart: unless-stopped
     depends_on:
      -  php-fpm
     ports:
      - 80:80
     volumes:
      - ./:/var/www/html
     environment:
       - DOCUMENT_ROOT=/var/www/html/public
       - CLIENT_MAX_BODY_SIZE=20M
       - PHP_FPM_HOST=php-fpm:9000 
     networks:
      - default

```

> P.S. please give a star if you like it :wink:


