## Start an already existed container

If we continue calling `docker run hello-world`{{execute}}, then a new container will be created each time, instead of reusing the ones we already have. 

A great solution is to use the `start` command. This command will start a stopped (exited) container, instead of creating a new one.

However if we run:
`docker start -i hello-world`{{execute}} (The -i flag will be explained in a later step, ignore it for now), it will show you an error message (What?? face),
```bash
Error: No such container: hello-world
```
even though the container has already been created! (We can see the container when we call `docker ps -a`{{execute}}).

The problem is that `hello-world` is the name of the image, not the container. So, we need to be specific and tell the docker which exact container we want to run, which can be specified via the **Container ID**.

We can find this ID through calling our favourite command: `docker ps -a`{{execute}}. The first column in the table show the ID for each container. So, find the ID to the container you want to start again and call `docker start -i `{{copy}} +  ContainerID.

However, that looks boring. Imagine having to do the same thing each time we want to run the container. Instead, docker allows for a nice and easy solution to this issue, by allowing the user to specify a name, or an alias, for the container. We can do this by using the following command:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker rename ContainerID NewName`{{copy}}, 

where ContainerID is the ID we can copy from `docker ps -a`{{execute}}

 **Note:** Docker actually gives the container a default name if no explicit name was given to the container during its creation. So what our command above actually did was to rename the container from the defualt given name (Ex. `heuristic_jepsen`), to `NewName`. This means that the command can be used multiple times, if the first name you gave it isn't to your liking anymore. In this case we can call: `docker rename NewName AnotherNewName`{{copy}}. or `docker rename ContainerID AnotherNewName`{{copy}}.

 We can also give the container a name directly when we create it by adding the flag `--name`: 

 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker run --name happy-world hello-world`{{execute}}, 
 
 where `happy-world` is the container's new name.

You can now call `docker start -i happy-world`{{execute}} (or whatever name you gave it) to start the container.

You can also see all these names you give to your container in `docker ps -a`{{execute}}.










----------------------------
