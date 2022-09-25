# Respository for PHP Distroless Images

This repository contains distroless images for PHP 8+.

Image will follow alpine package for php so there will be no PHP 7.4 version of this distroless php.
As soon as a new PHP version is given is alpine package it will be given in this repository.

For an Official PHP list of PHP supported version please go to this link :  
https://www.php.net/supported-versions.php

Nginx is already added to PHP-FPM images but you will need to provide your own default.conf for your website to be accessed.


To use the image build use the github container registry : https://ghcr.io/darkikim/php-distroless

Example docker-compose.yaml :  
```yml
version: '3.7'

services:
  distroless:
      restart: unless-stopped
      image: ghcr.io/darkikim/php-distroless:8.1-fpm
      ports:
        - "80:80"
      volumes:
        - ./webapp:/var/www
        - ./docker/config/default.conf:/etc/nginx/conf.d/default.conf
        - ./docker/config/nginx.conf:/etc/nginx/nginx.conf
```
nginx: [alert] could not open error log file: open() "/var/lib/nginx/logs/error.log" failed (13: Permission denied)
2022/09/25 14:38:56 [emerg] 367#367: mkdir() "/var/lib/nginx/tmp/client_body" failed (13: Permission denied)