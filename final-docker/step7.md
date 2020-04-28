## Listen and see the changes directly

Great! We can now run an apache server through docker. That is amazing. However we can still making this thing even more interesting and amazing.

Let's say that we are unhappy with the message we choose to display, and want to change it. 
- Call `vim src/index.php`{{execute}}
- type `i`{{execute}} to enter the insert mode
- Change the text that we echoed to anything else, E.g. `Hello, this should now be shown!` (Don't change anything else, keep the other commands as they were).
- Finally type `esc`{{execute}} and then `:wq`{{execute}}


We of course want this change to be shown to the people visiting our web server, but if you now go to the Dashboard again, and click the refresh button, nothing will change. This is because `src` was copied by the container, i.e. changes on the local machine won't be reflected in the running container. Imagine that you want to write a whole php and apache project. It will be very boring to repeatedly update the container every time you change something in the `src` folder, especially if you are debugging and trying to find some errors! 

Let's change this, and luckily for us, Docker offers a nice and easy solution to this issue, that make your changes appear as if it is synchronising with the docker container that is run. First, we'll stop the container via `docker stop my-running-app`{{execute}}.

Recall the command we used to run our container, `docker run -d --name my-running-app -p 80:80 my-php-app`. We will, with a slight modifcation, solve our problem! 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `docker run -d --name my-updated-running-app -p 80:80 -v /root/step6/src/:/var/www/html/ my-php-app`{{execute}}

The added section to our command is `-v /root/step6/src/:/var/www/html/`, and we will explain it in depth below (see header **Why did that happen?**). But first, lets just see that everything is working. Now if you refresh the Dashboard, you will obviously see the last change we have done to the index file, so lets change it again, and see if we can notice a difference!
- Call `vim src/index.php`{{execute}}
- type `i`{{execute}} to enter the insert mode
- Change the text that we echoed to any thing else, E.g. `Helloooo, from saammme index file` (Don't change anything else, keep the other commands as they were).
- Finally type `esc`{{execute}} and then `:wq`{{execute}}

You will see the same text appear to you in the Dashboard if you refresh it.

#### Why did that happen?

In order to understand what happened, we need to have an overview of how the Docker manage and store data.
All the files that are created inside a container are by default not persistent. That means all the files will be deleted when the container is removed.  

Docker has 2 main options to store files in the host machine and make the files created inside a container persistent. These 2 options can basically created a shared storage between both the container and the host machine.

The first option is called `volume`, while the second is called `bind mount` (this is the option we used to solve our problem above). (Actually there is also a third option called `tmpfs mount` but it doesn't work on all operating systems, so we are going to ignore it in this tutorial). 

#### Difference between `volume` and `bind mount`
The following image can help us illustrate the difference between the 2 options:

![types-of-mounts](./assets/types-of-mounts.png)

- `volumes`: are stored in a specific place inside the host system (E.g. in linux it is usually `/var/lib/docker/volumes`) that is managed by Docker itself. The other processes (that are non-Docker) shouldn't edit this folder (or filesystem).  You can manually create a volume or Docker can itself create one during the creation process of the container.

- `bind mounts`: mount a file or a folder to the container using the full path. That means the files/folder can be anywhere in your system and it isn't managed by Docker itself. However, you should be careful using bind mount since you actually change the host filesystem via the processes running in the container (creating, changing or deleting important system files or directories).

In general `volumes` have more functionality than `bind mounts`.
E.g. A volume can be used to mount multiple containers with each others simultaneously. For more information about that you can check the [documentation](https://docs.docker.com/storage/)


#### The `-v` flag
Back to the command we wrote:
`docker run -p 80:80 -v /root/step6/src/:/var/www/html/  my-php-app`

I have mentioned that we are using `bind mount` to mount a folder in our file system (in our host machine) which is in our case: `/root/step6/src`. This directory will now be shared between the container and our host machine. The second path written in the command (`/var/www/html/`) is the path where our folder (`src`) will be mounted in the container we created.

And thus now any changes we will make in the `src` folder will directly be modified in the container and we can directly see it in the Dashboard.













-----------------------------
