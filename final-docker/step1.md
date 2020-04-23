## Create a container and run it

Let's start by looking at all the images installed on the machine! We can achieve this goal by issuing the following command on the terminal (or by pressing the command below):

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker images`{{execute}}.

We can see that Katacoda has a few images installed already! An image is an executable package of software that contains the required components for the applicaiton, i.e. the code, system libraries, settings, etc. One clould look at them as instructions for how a container should be contstructed, because thats what happens when you run an image on the Docker Engine! From an OOP perspective, the image would be equated to the object class definition, while the container would be the instance of it (**Note:** you could have multiple instances, i.e. containers stemming from the same image).

Now that we know the difference betweeen an `image` and a `container`, let's also list all of the currently available containers (**Note:** the `-a` flag basically means show all containers): 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker ps -a`{{execute}}

Unsurprisingly, since we haven't created any container yet, we will see that the list is empty. Let's change that! We can try to install another image and create a container of it and see what will happen. Since programmers love to begin with hello-world, let's do that as well. Run:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker run hello-world`{{execute}}

This command will try to find the image `hello-world` locally, and then **create** a container and finally **run** it. But since we haven't installed this image before, it won't find anything locally! However, docker is very nice and great, so even if it didn't find the image locally, it will search for it in a database on the internet called `docker hub`, and download it from there!
Once the image is found, a container of this image is created.

Another nice thing about docker is that it prints a message to you that explain to you what has just happened with more details:

```bash
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:f9dfddf63636d84ef479d645ab5885156ae030f611a56f3a7ac7f2fdd86d7e4e
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

Now, if when we run

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker images`{{execute}}, 

we can see the image `hello-world`! 

We can also see that a container of this image has been created by running: `docker ps -a`{{execute}} again. Some additional infromation we can see is the weird name the container has been given, as well as the fact it was executed and exited recently.

**Note**, if you now want to rerun this container (`docker run hello-world`{{execute}}), you will notice that it's much faster. This is because we now have already installed the image, and that step can be skipped entirely. Another thing that you can notice is that another container of the same image has been created (if you call `docker ps -a`{{execute}} again).

That is because the command `run` don't just run (start) a container, it also **create** a container (regardless if there is a pre-created container or not).

In the next step, I will explain how we can start an already exited container, and also how to remove one.









--------------------------
