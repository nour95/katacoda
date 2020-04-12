# Some basic commands (to be moved to step 2)

We can see all the images that had been installed in your system, you can run:
`docker images`{{execute}}.

Here we can see that Katacoda has many already installed images. But has no ready containers (pre-created containers).

We can see all the container that have been created in your system through running:
`docker ps -a`{{execute}}

Since we haven't created any container yet, we will see that the list is empty.
<!---
TODO diff between images and containers.
https://www.edureka.co/community/18657/what-is-the-difference-between-a-docker-image-and-container
-->

We can now try to install another image and create a container of it and see what will happen.
Since programmers love to begin with hello-world functions/things, let's install a hello-world image. Run:
`docker run hello-world`{{execute}}

This command `run` will try to find the image `hello-world` locally and then **create** a container and **run** it. But since we hadn't install this image before, it won't find anything.

However docker is very nice and great so even if it didn't find the image locally, it will search about it in a database on the internet or what is called: docker hub.
Docker search there and find such image and install it. Then it create a container of this image.

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

Now if when we run: `docker images`{{execute}}, we can see the image `hello-world` between the images.

We can also see that a container of this image has been created by running: `docker ps -a`{{execute}}.
We can see that this container has a wired name and that it had been executed and exited from few seconds ago.

**Note**, if you now want to rerun this container and called:
`docker run hello-world`{{execute}}, you will note that this happen faster (since we now have already installed the image). Another thing that you can notice is that another container of the same image has been created (if you call `docker ps -a`{{execute}} again).

That is because the command `run` don't just run (start) a container, it also **create** a container (create one regardless if there is a pre-created container or not).

In the next step, I will explain more how we can start an already exited container and how to remove one.









--------------------------
