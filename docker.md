## Build Commands

`docker build`

Builds an images from the Dockerfile in the current directory
```
docker build https://github.com/docker/rootfs.git#container:docker
```

Builds an image from a remote GIT repository

`docker build -t imagename/tag`

Builds, and tags an image for easier tracking

`docker build https://yourserver/file.tar.gz`

Builds an image from a remote tar archive

```
docker build -t image:1.0 -<<EOF
FROM busybox
RUN echo “hello world”
EOF
```

Builds an image via a Dockerfile that is passed
through STDIN 

## Clean Up Commands

`docker image prune`

Clears an unused image

`docker image prune -a`

Clears all images that are not being used by
containers

`docker system prune`

Removes all stopped containers, all networks
not used by containers, all dangling images, and
all build cache

`docker image rm image`

Removes an image

`docker kill $ (docker ps -q)`

Stops all running containers

`docker stack rm stackname`

Removes a swarm

`docker volume rm $(docker volume ls -f dangling=true -q)`

Removes all dangling volumes

`docker rm container`

Removes a running container

`docker kill $ (docker ps -q)`

Stops all running containers

## Container Interaction Commands

`docker start container`

Starts a new container

`docker stop container`

Stops a container

`docker pause container`

Pauses a container

`docker unpause container`

Unpauses a container

`docker restart container`

Restarts a container

`docker wait container`

Blocks a container

`docker export container`

Exports container contents to a tar archive

`docker attach container`

Attaches to a running container

`docker wait container`

Waits until the container is terminated and
shows the exit code

```
docker commit -m “commit message”
-a “author” container username/
image_name: tag
```

Saves a running container as an image

`docker logs -ft container`

Follows container logs

`docker exec -ti container script.sh`

Runs a command in a container

`docker commit container image`

Creates a new image from a container

`docker create image`

Creates a new container from an image

## Container Inspection Commands

`docker ps`

Lists all running containers

`docker -ps -a`

Lists all containers

`docker diff container`

Inspects changes to directories and files in the container filesystem

`docker top container`

Shows all running processes in an existing container

`docker inspect container`

Displays low-level information about a container

`docker logs container`

Gathers the logs for a container

`docker stats container`

Shows container resource usage statistics

## Manage Images Commands

docker image ls
Lists images
docker image rm mysql
Removes an image
docker tag image tag
Tags an image

docker history image
Displays the image history
docker inspect image
Displays low-level information about an image

## Run Commands
Docker uses the run command to create containers from provided images. The default syntax for this
command:

`docker run [options] image [command] [arg...]`

Then you can use one of the following flags:

`--detach , -d`

Runs a container in the background and prints the container ID

`--env , -e`

Sets environment variables

`--hostname , -h`

Sets a hostname to a container

`--label , -l`

Creates a meta data label for a container

`--name`

Assigns a name to a container

`--network`

Connects a container to a network

`--rm`

Removes container when it stops

`--read-only`

Sets the container filesystem as read-only

`--workdir , -w`

Sets a working directory in a container


## Registry Commands

`docker login`

Log ins to a registry

`docker logout`

Logs out from a registry

`docker pull mysql`

Pulls an image from a registry

`docker push repo/ rhel-httpd:latest`

Pushes an image to a registry

`docker search term`

Searches Docker Hub for images with the specified term

## Service Commands

`docker service ls`

Lists all services running in a swarm

`docker stack services stackname`

Lists all running services

`docker service ps servicename`

Lists the tasks of a service

`docker service update servicename`

Updates a service

`docker service create image`

Creates a new service

`docker service scale servicename=10`

Scales one or more replicated services

`docker service logs stackname`

`servicename`

Lists all service logs

## Network Commands

`docker network create networkname`

Creates a new network

`docker network rm networkname`

Removes a specified network

`docker network ls`

Lists all networks

`docker network connect networkname container`

Connects a container to a network

`docker network disconnect networkname container`

Disconnects a container from a network

`docker network inspect networkname`

Displays a detailed information about a network

## Creating Volume
Volume is simply a directory inside our container
- Fistly, We have to declare this directory as a volume and then share volume
- Efen If we stop container, still access volume
- Volume will be created in container
- You can declare a directory as volume only while creating container
- You can't create volume from existing container
- You can share one volume across any number of containers
- Volume will not be included when you update an image

You can mapped volume in two ways:
1. Container <--> Container
2. Host <--> Container

### Benefits of volume
- Decoupling container from storage
- Share volume among different containers
- Attach volume to containers
- On deleting container volume does not delete

1. Volume (Container <--> Container)

Create d `Dockerfile` and write
```
FROM ubuntu
VOLUME ["/myvolume1"]
```
then create image from this `Dockerfile`

`docker buid -t myimage`

now create a container from this image & run

`docker run --it --name container1 myimage /bin/bash`

now do `ls`, you can see `myvolume1`

### share volume with other container Container <--> Container

`docker run -it --name container2(new) --privileged=true --volumes-from container1 ubuntu /bin/bash`

Now after creating container2 myvolume1 is visible whatever you do in one volume, can see from other volume

- touch filex  filey  filez
- docker start container1
- docker attach container1
- ls/myvolume1  #you can see samplefile here filex  filey  filez

Now, try to create volume by using commands

`docker run -it --name container3 -v /volume2 ubuntu /bin/bash`

Do `ls` and `cd` volume2 and then create one file `cont3file` and exit
now create one more container, and share volume2

`docker run -it --name container4 --priveleged=true --volumes-from container 3 ubuntu /bin/bash`

Now you are inside `container4`, do `ls`, you should see `volume2` `cd` to `volume2` and create few sample files eg. `sample1` `sample2`, `sample3` and do `ls` to verify

go back to `container3` and navigate to volume2 folder, you should see `sample1` `sample2` and `sample3` files

2. Volume (Host <--> Container)

Create and verify few files in 
`/home/host-user` this is your host folder path(can be anywhere in the host)

`docker run -it --name hostContainer -v /home/host-user:asansari --privileged=true ubuntu /bin/bash`

`:asansari` is `hostContainer` path

`cd asansari`

Do `ls`, now you can see all files of host machine now let's try to create one file under `hostContainer` volume folder and then `exit`
Now go back to your host folder `/home/host-user`, you can see this file
 







