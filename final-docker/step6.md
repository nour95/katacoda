## Build a slightly more interesting container

Create an easy web server through docker, that listen to port 80:
1. Create php file `index.php` in `/src`

```php
<?php
echo "Some message";
```

2. Create Dockerfile:

```
FROM php:7.0-apache
COPY src/ /var/www/html
EXPOSE 80
```
* Find php image from dockerhub
* Follow the instructions from php dockerhub, like directory naming etc
* EXPOSE 80 --> The container will listen on port 80
3. docker build -t new_container .
4. docker run -p 80:80 new_container
    - -p 80:80 --> from port 80 on the host to port 80 in the container
5. If we now click on the Dashboard button, which can be found next to the Terminal that we have been using so far, we can see that our message can be seen there!


<!--
TODO to run and move the container to somewhere else:
docker run -it --name my-linux --rm -v /root/nourTest/:/my-data ubuntu bash
-->

<!--
TODO what are the differences between bind mount and volume when running a container
-->








//-------------------------------
