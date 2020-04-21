## build your own container
a simple version

After we understand how to install an image, create a container, start it, remove it and rename it. It is time to learn how to build your own image that you can share on docker hub or send it to the other people.

To build your own container you need to create a file called exactly `Dockerfile` (**Note:** Dockerfile should have no extensions and begin with capital D). It can also be good to create a folder and put the Dockerfile in it. So call `mkdir myDocker`{{execute}}. Then: `cd myDocker`{{execute}} and finally `touch Dockerfile`{{execute}}.

Inside the Dockerfile, we need to type a few things, so let's edit the file first `vim Dockerfile`{{execute}}.
Type `i` to enter insert mode and then write the following:

`FROM ubuntu`{{execute}}
However we want to see our own container do something, something simple. Thus in the next line type:
`CMD echo "Hello, Happy to see you"`{{execute}}(or any other message).

then trype `esc` to escape the insert mode and then type `:wq` to save the changes.

<!--
TODO May be we don't need to mention the vim instructures (the problem is that in the creteria they wrote that the TA need to be able to run all the commands and able to do everything and I am not sure if some TA may don't know how to use vim)
-->

But what does that mean? and What is a Dockerfile in the first place?
Well Dockerfile contains a collection of  Dockerfile commands and operative system command such as Linux. This file is very necessary to build our container and it tells `docker build` command (that build a container) which containers will our container based on, what this container do, and so on.

<!--
TODO May be the explanation above is also too much
-->

 `FROM`, The first command in the Dockerfile means `The base image for building a new image`. We need a point to start from. We need a base image to make our build. Here in this simple example, We choose to use the image `ubuntu` (there are other ways and tutorial that can explain how to create a base image so you want to create something that based on a very unique things so don't worry).

 The next line contain 2 part:
 - The `echo "Hello, Happy to see you"` and this is an obvious Linux command that will just print `Hello, Happy to see you"` to you.
 - The `CMD` command which is a dockerfile command that can be used,  according to [theNewStack](https://thenewstack.io/docker-basics-how-to-use-dockerfiles/), to execute a specific command such as `echo` within the container we want to build.


 **Note** there is little similar commands that one can see in other tutorial called `RUN`. This command basically can basically according [howToForge](https://www.howtoforge.com/tutorial/how-to-create-docker-images-with-dockerfile/) execute a command **during** the build process of the docker image. E.g. we can use it to update software repository in the ubuntu image as the following:
 `RUN apt-get update`{{execute}}.

 <!--
 TODO Add the answer to the question: "what are the differences between RUN and CMD in a Dockerfile" here.
 https://www.howtoforge.com/tutorial/how-to-create-docker-images-with-dockerfile/

 https://thenewstack.io/docker-basics-how-to-use-dockerfiles/

In the line 35, I wrote some outlines but not sure if the explanation need to be better (have a better comparsion) or the reference need to be better. I had also copied and pasted things dirctly without various changes.
 -->


However, now we are done with creating a dockerfile, let's us build our own amazing image.

Make sure to be in the directory that contain the `Dockerfile` and then call:
`docker build -t my-first-image .`{{execute}}
and make sure to not forget the point at the end.

Some general notes about the previous command:
- The `.` at the end of the commend represent the location. and since we are in the same folder as the Dockerfile, we type just a point.
- Here, the `-t` flag means the name of the your new image. In the [documentation](https://docs.docker.com/engine/reference/commandline/build/) they wrote that `-t` flag means more specifically: `Name and optionally a tag in the ‘name:tag’ format`. But I think it is simpler to think about it just as a name.
- The image name must be in lowercase and it can have any other name (not necessary `my-first-image`)

Now if we call:
`docker images`{{execute}} we can see our amazing image `my-first-image` between the images. And if we call: `docker run -it my-first-image`{{execute}}

Now, We can see that the image printed the sentences we want and we wrote in the Dockerfile: `Hello, Happy to see you`.



------------------------------
