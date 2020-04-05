# First commands:

- show all docker images:
docker ps -a


- run a docker with a bash:
docker run -it --name my-linux ubuntu bash

- to exit the docker type: exit

- to give the container a name add the flag --name theNameYouWantToGive

- To show all the images that you have, run:
docker images

- To delete a container, type:
docker rm $(docker ps -a -f status=exited -q)

- To stop a running container:
docker stop my-linux


- To run a container and remove it at the same time:
docker run -it --name my-linux --rm  ubuntu bash

- to run and move the container to somewhere else:
docker run -it --name my-linux --rm -v /root/nourTest/:/my-data ubuntu bash

- to build a container:
-- create a file called Dockerfile , and write on it:
FROM ubuntu
CMD echo "Hello Nour, Happy to see you"
then call
-- docker build -t nour-ubuntu .
and don't forget the point at the end

- to test your build is working: type
docker run -it nour-ubuntu


begin by this:
https://www.youtube.com/watch?v=JprTjTViaEA&t=642s

then this:
https://www.youtube.com/watch?v=YFl2mCHdv24

















////--------------------------
