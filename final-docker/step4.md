## Remove containers and images

So now, we can see that there are many containers has been created and the list became quite long. We can also note that it is sometimes more complicated to start some container using the `start` command.

E.g. if you call `docker start -i ubuntu`{{execute}}, the interface won't be interactive or friendly. you can still call common terminal commands like: `cd`{{execute}}, `ls`{{execute}}, `mkdir newFolder`{{execute}},... etc. You can also exit the container through calling `exit`{{execute}}.

The interface won't be so friendly because we didn't use the `-t` flag and that simply because the `start` command don't have this flag.

<!--
TODO not sure if it is good to mention that start won't work with the ubuntu
-->

Thus, sometimes it is easier to use the `run` command. In this case we need to have a way to remove the unnecessary containers or the containers that we are not going to use again.

We can remove things using the `rm` command. E.g.
- `docker rm `{{copy}} +  ContainerID,
- or `docker rm `{{copy}} + the name you give to the container. e.g. `docker rm happy-world`{{copy}}.

However, it is little boring to remove every container by itself. that will take a lot of time. However docker is so nice and there is a way that we can use to fix this issue.
- We can remove all the exited container by call:
`docker rm $(docker ps -a -f status=exited -q)`

**Note** we have used the `-f` flag that means according to the
[documentation](https://docs.docker.com/engine/reference/commandline/ps/): `Filter output based on conditions provided`

Here: we want to remove all the exited container and thus we choose the condition to be: `status=exited`, meaning all the container that has the status exited.

<!--
TODO Maybe the explanation to the condition is too much?  it is very clear?
-->

But, as we saw before the `rm` command needs IDs (or alias names that you already give to the container) to know what to remove. Thus, we need to use the flag `-q` which means `Only display numeric IDs`. You can also note that if you call `docker ps -a -q`{{execute}}, we can see it return only the IDs. Thus, now `$(docker ps -a -f status=exited -q)` will return the needed inputs to the `rm` command.


However, This still looks boring, every time we are done with all containers and want to go home, we need to call another command and remove everything.

The nice docker can help us to do this faster by adding the flag `--rm` when we call the `run` command. E.g. we can call:
`docker run -it --rm  ubuntu`{{execute}}. What will happen here is that docker will `automatically remove the container when it exits`.

**Note:** you need to type `exit` first and then call `docker ps -a`{{execute}} to see this working (that the previous ubuntu container that has been created, has been removed automatically).





-------------------------------
