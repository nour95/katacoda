## Build your own container
After we understand how to install an image, create a container, start it, remove it and rename it. It is time to learn how to build your own image that you can share on docker hub, or use yourself!

To build your own container you need to create a file called exactly `Dockerfile` (**Note:** Dockerfile should have no extensions and begin with capital D). It can also be good to create a folder and put the Dockerfile in it. So call `mkdir myDocker`{{execute}}. Then: `cd myDocker`{{execute}} and finally `touch Dockerfile`{{execute}}.

Inside the Dockerfile, we need to type a few things, so let's edit the file via `vim Dockerfile`{{execute}}.
Type `i` to enter insert mode and then write the following:
1. `FROM ubuntu`{{execute}}
2. `CMD echo "Hello, Happy to see you"`{{execute}}(or any other message)
3. Then type `esc` to escape the insert mode and then type `:wq` to save the changes.

The first command in the Dockerfile, `FROM`, means `The base image for building a new image`. We need a point to start from, and why not use the `ubuntu` image we have some familiarity with!(There are other ways and tutorials that can explain how to create a base image, so if you want to create something based on a very unique thing there's no need to worry).

The next line contain 2 parts:
- The `echo "Hello, Happy to see you"`, which is an obvious Linux command that will just print `Hello, Happy to see you"`.
- The `CMD` command's purpose is to set a default instruction to execute when the container is ran (without an explicit flag overriding this default execution), which in this case is `echo "Hello, Happy to see you"`


**Note** there is little similar commands that one can see in other tutorial called `RUN`. This command basically can basically according [howToForge](https://www.howtoforge.com/tutorial/how-to-create-docker-images-with-dockerfile/) execute a command **during** the build process of the docker image. E.g. we can use it to update software repository in the ubuntu image as the following:
`RUN apt-get update`{{execute}}.

<!--
TODO Add the answer to the question: "what are the differences between RUN and CMD in a Dockerfile" here.
https://www.howtoforge.com/tutorial/how-to-create-docker-images-with-dockerfile/

https://thenewstack.io/docker-basics-how-to-use-dockerfiles/

In the line 35, I wrote some outlines but not sure if the explanation need to be better (have a better comparsion) or the reference need to be better. I had also copied and pasted things dirctly without various changes.
 -->


Now that we're done with creating the dockerfile, let's build our own amazing image.

Make sure to be in the directory that contain the `Dockerfile` and then call:
`docker build -t my-first-image .`{{execute}}
and make sure to not forget the dot at the end.

Some general notes about this command:
- The `.` at the end of the commend represent the location of the `Dockerfile`, i.e. the current directory
- Here, the `-t` flag allows us to name our image 
    - The name must be in lowercase, other than that it's up to the user (`my-first-image` is our suggestion, since that is the name we will be using going forward in this tutorial)

Now if we call:
`docker images`{{execute}} we can see our amazing image `my-first-image` listed, and if we call

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker run -it my-first-image`{{execute}},

we can see that the image printed the message we wrote in the Dockerfile: `Hello, Happy to see you`.



------------------------------
