## Build a slightly more interesting container
Let's move on to something a little bit more interesting, by creating a container running a web server!

First, let's create the application we want our server to run. For simpicity's sake, we will keep it simple and just print a message of your choosing. For reasons that will be explained later, we need to create a directory called `/src`, so let's do so by calling:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `mkdir src`{{execute}}

We will write our basic program in php:
```php
<?php
echo "Some message";
```

Recall how this was done in the previous step:  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `vim index.php`{{execute}}

Enter insert mode by påressing `i`, and write 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `<?php`{{execute}}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `echo "Some message"`{{execute}}

Then press `esc`, followed by `:wq` to leave and save the file. 

Next we want to create the Dockerfile for our new contianer. It should look like this, and can be created just as the php file was:
```
FROM php:<version>-apache
COPY src/ /var/www/html
EXPOSE 80
```

So, before you jsut copy and paste this in, let's take a closer look at each of the lines, and understand why they are as they are. So, as we know, we need a base layer to build upon for our new image, and we want our container to function as a web server for an application written in `php`. Lucky for us, a perfect image to build from is accesible on the docker hub! So let's visit `https://hub.docker.com/`, and search for `php`. What we will find is that there is an official `php` image. Now this page contain documention for how the image should be used, as well as some different variants of the image itself, each designed for different purposes. Since we would like to create a web server, we will go with the `apache` variant! By scrolling down a bit on the page, the isntructions for how this image should be used can be found (the `php:<version>-apache` header). These instructions cover the 2 first lines of our Dockerfile (**Note** that the version must be specified in the Dockerfile as well). The last line quite simply results in the container to listen on port 80.

Now, lets continue following the intructions from the documentation. To build our image, simply call:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker build -t my-php-app .`{{execute}}

Remember, `-t` is the flag that allows us to name our image. 

And now, there is only one real step left, to run our new container. But first, how do we see that everything is working as expected? This tutorial is written for Katacoda, and Katacoda offers a simple soultion for this problem. If you press the button `Dashboard` on top of the page, you will be able to connect to a specific port. Port 80 should already be selected, but make sure that it actually is! So, now we can run the container:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker run -d --name my-running-app -p 80:80 my-php-app`{{execute}}

The `-d` flag allows the container to run in detached mode, i.e. the container will run in the background, while the `-p` flag forwards port 80 of the host to the exposed port 80 in the container. Let's also take a look at our running containers:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker ps`{{exectute}}

We can see that our container is running, and if you once again press the `Dashboard` button, we can see that our message is indeed shown!





//-------------------------------
