## Start an already existed container

If we just continue calling `docker run hello-world`{{execute}} every time we want to run this container, this will also increase the stack of the containers and won't reuse things that we have already.

A great solution is to use the `start` command. This command won't create a new container, it will started any stopped (exited) containers.

However if we run:
`docker start -i hello-world`{{execute}} (I will explain the flag -i in the next step), it will show you an error message (What?? face),
```bash
Error: No such container: hello-world
```
even if the container has already been created (We can see the container when we call `docker ps -a`{{execute}}).

The problem is because 'hello-world' is the name of the image, not the container. So, we need to be specific and tell the docker which container we exactly want to run. We can do this by telling docker the **Container ID**.

We can find the container ID through calling our favourite command: `docker ps -a`{{execute}}. The first column, in the table of the container show the container ID for each container. So, find the ID to the container you want to start again and call `docker start -i `{{copy}} +  ContainerID.

However, that looks boring. Imagine that we need to do the same thing many times. each time we need to copy remember the ID of the container and then start it again.

Thus, docker can give you a nice solution to this issue. Basically, we can give the container a name (an alias).

We can give a name to a docker container, using the following command:
 `docker rename ContainerID NewName`{{copy}}, where ContainerID is the ID we can copy from `docker ps -a`{{execute}}

 **Note:** the previous command can be also used to rename a container which already had a name. In this case we can call: `docker rename NewName AnotherNewName`{{copy}}. or `docker rename ContainerID AnotherNewName`{{copy}}.

 We can also give the container a name directly when we create it first time by adding the flag `--name`.
 E.g.
`docker run --name happy-world hello-world`{{execute}}, where `happy-world` is the container's new name.


You can now call `docker start -i happy-world`{{execute}} or whatever name you give to the container to start it.

You can also see all these names you give to your container in `docker ps -a`{{execute}}.










----------------------------
