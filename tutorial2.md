- in
https://hub.docker.com/_/php
- then:
https://github.com/docker-library/docs/blob/master/php/README.md#supported-tags-and-respective-dockerfile-links

- find 7.4-apache

- to save and exit in vim, write: :wq

- in the file Dockerfile ()has no extensions and begin with capital D, write:
FROM php:7.4-apache
COPY src/ /var/www/html/
EXPOSE 80

- then build your container with:
docker build -t nour-php .
(and don't forget the point at the end)

- run your container:
docker run -p 80:80 nour-php


- To see a live changes, run your container:
docker run -p 80:80 -v /root/nourDocker/src/:/var/www/html/  nour-php













///==================
