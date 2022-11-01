![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jkaninda/nginx-fpm?style=flat-square)
![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/jkaninda/nginxp-fpm?style=flat-square)
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
       - DOCUMENT_ROOT=/var/www/html/
       - CLIENT_MAX_BODY_SIZE=20M
       - PHP_FPM_HOST=php-fpm-host:9000 
     networks:
      - default

```
> P.S. please give a star if you like it :wink:


