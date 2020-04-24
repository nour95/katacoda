## Remove containers and images

So now, we can see that there are quite a few containers created on the the system (via `docker ps -a`{{execute}}). So not to clutter up the system, we need to have a way to remove the unnecessary and unwanted containers.

We can do this by using the `rm` command. E.g.
- `docker rm `{{copy}} +  ContainerID,
- or `docker rm `{{copy}} + the name you give to the container. e.g. `docker rm happy-world`{{copy}}.
**Note**: A list of containter Names/ID:s can also be used


However, it is quite tedious to remove every container by individually. Fortunately, Docker offers a solution for this problem! It is possible to use filters in docker, so let's for example say we would like all exited containers to be removed, we could use the following command, :

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker rm $(docker ps -a -f status=exited -q)`{{execute}}

**Note** we have used the `-f`: `Filter output based on conditions provided` and `-q`: `Only display numeric IDs` (which  will be explained below) flags to achieve our goal. If you are interested to learn more, check out the documentation for the `docker ps` command 
[here](https://docs.docker.com/engine/reference/commandline/ps/). 

But, as we saw before the `rm` command needs IDs (or aliases) to know what to remove. Thus, we need to use the flag `-q`, which only returns the ID:s of the containers matching the filter. You can also note that if you call `docker ps -a -q`{{execute}}, we can see it return only the IDs. Thus, `$(docker ps -a -f status=exited -q)` will return the needed inputs to the `rm` command.

However, this still looks boring, every time we are done with all containers and want to go home, we need to call another command and remove everything.

The nice docker can help us to do this faster by adding the flag `--rm` when we call the `run` command. E.g. we can call:
`docker run -it --rm  ubuntu`{{execute}}. What will happen here is that docker will `automatically remove the container when it exits`.

**Note:** you need to type `exit` first and then call `docker ps -a`{{execute}} to see this working (that the previous ubuntu container that has been created, has been removed automatically).





-------------------------------
