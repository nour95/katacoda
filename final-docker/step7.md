## listen and see the changes directly

<!-- list on port 80 and update the things directly

TODO Another good site that explain how to remove images:
https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/#remove-one-or-more-images

docker image rm imageID
-->


Great! We can now run an apache server through docker. That is amazing. However we can still making this thing even more interesting and amazing.

Open another terminal in Katacoda, you can do this through clicking the plus sign next to Dashbord as the image below:

![plus-sign](./assets/.png) TODO add an image

Then choose `Open New Terminal`

In this new terminal called `Terminal 2` change the `index.php` file.

- Call `vim myPHP/src/index.php`{{execute T2}}
- type `i`{{execute T2}} to enter the insert mode
- Change the text that we echoed to any thing else, E.g. `Hello 2, from same index file` (Don't change anything else, keep the other commands as they were).
- Finally type `esc` and then `:wq`{{execute}}

Now if you go to the Dashbord again and clicked the refresh button, nothing will change. You need basically to click `^C` in the Terminal 1 to stop container and exit it. and then rebuild the image and recreate a container.

Imagine that you want to write a whole php and apache project. It will be very boring to do so every time you change something in the in the `index.php` or in the `src` folder, Especially if you are debugging and trying to find some errors.

There is a nice very easy solution to this issue that make your changes appear as if it synchronising with docker container that is run.

basically go back to `Terminal 1` (called only in the `Terminal` in Katacoda) and stop the running container using `^C`{{execute T1}} or ( `control + c` if you are using Windows).

<!--TODO not sure what is the command to stop a process in Windows
-->

Then instead for running the container using the `run` command used in  step 6: `docker run -p 80:80 my-php`, call this instead:
`docker run -p 80:80 -v /root/myPHP/src/:/var/www/html/  my-php`{{execute T1}}.

// I am just testing that this is working, I will continue writing:
- example to see this happen
- explain the -v flag and what happened in the last command
- diff between bind mount and volume










<!--
TODO what are the differences between bind mount and volume when running a container
-->






//-----------------------------
