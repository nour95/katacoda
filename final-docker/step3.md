## Install and run another container

Let's now do something a little bit more complicated and interactive that we can use and see. Now, after we have learnt some basic commands, we can move on from the `Hello world` program to the next step.

So first, let's create a container that can run an ubuntu terminal (e.g. if you have mac or you want to run some command in a terminal or if you want to do some other complicated things as we will see in a later step). Call:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker run -it ubuntu`{{execute}}.

**Note**: in some tutorials on the internet, you may find that they call `docker run -it ubuntu bash`{{execute}}. Adding `bash` specifies to docker that `bash` should be run in the `ubuntu` container. However, since `bash` is the default command to run in the currently available docker image on the docker hub ([April 2020]), the commands will essentially have identical outcomes. Do note that this may change in the future however, so by explicitly stating that `bash` should be run is the safer option. 

If you don't believe me, you can also see this under the column `COMMAND` when we call: `docker ps -a`{{execute}}, where we can see that `bash` is indeed the default command! 

<!--
TODO is this link necessary? I don't think so
You can read more about that [here](https://askubuntu.com/questions/938869/docker-run-ubuntu-bin-bash-vs-docker-run-ubuntu).
TODO is this explanation after the link also necessary? I don't think so
-->

Inside this container you can call all the normal and common terminal commands like: `cd`{{execute}},`ls`{{execute}},... etc. So, for instance, let's create a folder inside of our new container called `test`, and see if it is persistant.

1. First we need to make sure there isn't such a folder already! 
    * `ls`{{execute}}
    * Great, there is no folder named `test` here!
2. Now create the directory
    * `mkdir test`{{execute}}
    * Now there is!
3. Play around to your own liking, and when you feel satisfied, feel free to `exit`{{execute}}
4. Lets once again start the container, to do so we need to remember what we learnt in step 2.
    * `docker ps -a`{{execute}}
    * See which container was exited last
    * `docker start -i ContainerID`{{copy}} or `docker start -i ContainerName`{{copy}}
5. Finally, lets see if the directory can be found
    * `ls`{{execute}}
6. And there it is!

### What do the flag the -i and -it do?

The flag `-i` will connect the STDIN of the command inside the container to the STDIN of the docker run itself.

The flag `-t` will tell the main process inside docker that its input is a terminal device.

These two in combination will allow us to use the termial inside the container as a "normal" terminal (similarly to when connecting via `ssh`).

For more information about that, check [this discussion](https://stackoverflow.com/questions/30137135/confused-about-docker-t-option-to-allocate-a-pseudo-tty)

<!--
TODO Do I need too explain this more? I don't think so. I think having the link is good though, as this topic is a bit more complicated than the one before
-->













----------------------------
