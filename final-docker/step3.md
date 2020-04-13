## Install and run another container

Let's now do something little more complicated, something little more interactive that we can use and see. Now, after we had learnt some basic commands, we can move on from `Hello world` program to the next step.

So let's create a container that can run an ubuntu terminal (e.g. if you have mac or you want to run some command in a terminal or if you want to do some other complicated things as we will see in a later step).

Call:
`docker run -it ubuntu`{{execute}}.

**Note**: in some tutorial in the internet, you may found that they call `docker run -it ubuntu bash`{{execute}}. In the current version of image (all the version until now [April 2020]) the docker hub, the default command to run in the ubuntu image is `bash`. You can read more about that [here](https://askubuntu.com/questions/938869/docker-run-ubuntu-bin-bash-vs-docker-run-ubuntu).

You can also see this under the column `COMMAND` when we call: `docker ps -a`{{execute}}, there we can see that the default command is `/bin/bash`. If you run `docker run -it ubuntu bash`{{execute}}, you will also see a similar command when you run
`docker ps -a`{{execute}}, basically `bash`.
<!--
TODO is this link necessary?
TODO is this explanation after the link also necessary.
-->

Inside this container you can call all the normal and common terminal commands like: `cd`{{execute}},`ls`{{execute}},`mkdir newFolder`{{execute}},... etc.

However, After you are done, you can exit the container and its terminal/bash by typing `exit`{{execute}}.


### What do the flag the -i and -it do?

The flag `-i` will connect the STDIN of the command inside the container to the STDIN of the docker run itself.

The flag `-t` will tell the main process inside docker that its input is a terminal device.

For more information about that, check [this discussion](https://stackoverflow.com/questions/30137135/confused-about-docker-t-option-to-allocate-a-pseudo-tty)

<!--
TODO Do I need too explain this more?
-->













----------------------------
