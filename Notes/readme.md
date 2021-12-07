# Docker
Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a given host. Containers are lightweight and contain everything needed to run the application, so you do not need to rely on what is currently installed on the host. You can easily share containers while you work, and be sure that everyone you share with gets the same container that works in the same way.

![VM VS CONTAINER](https://github.com/DRoyyy/Docker-Stuff/blob/main/Notes/images/vm-vs-container.png)


## Docker Architecture
Docker uses a client-server architecture. The Docker *client* talks to the Docker *daemon*, which does the heavy lifting of building, running, and distributing your Docker *containers*. The Docker *client* and *daemon* can run on the same system, or you can connect a Docker *client* to a remote Docker *daemon*. The Docker *client* and *daemon* communicate using a REST API, over UNIX sockets or a network interface. Another Docker *client* is Docker *Compose*, that let you work with applications consisting of a set of *containers*.

![Docker Architecture](https://github.com/DRoyyy/Docker-Stuff/blob/main/Notes/images/architecture.svg)

### daemon
The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

### client
The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

### Registry
A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry. When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry.

### Images
An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

### Containers
A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

By default, a container is relatively well isolated from other containers and its host machine. You can control how isolated a container’s network, storage, or other underlying subsystems are from other containers or from the host machine.

A container is defined by its image as well as any configuration options you provide to it when you create or start it. When a container is removed, any changes to its state that are not stored in persistent storage disappear.


## Some Basic Docker Commands

### Find the version
    $ docker --version

### Get detailed information about docker installed on the system
    $ docker info

### Pull image
    $ docker pull <imagename>                     //exclude <> 

### List all the docker images
    $ docker images

### Run the docker image
    $ docker run -it -d <imagename>

### Lists all the running docker containers
    $ docker ps

### List all the docker containers running/exited/stopped
    $ docker ps -a

### Access the docker container and run commands inside the container
    $ docker exec -it <containerid> bash

### Starts the docker container with container id
    $ docker start <containerid>

### Stop a container with container id
    $ docker stop <containerid>

### Restart the docker container with container id
    $ docker restart <containerid>

### Remove stopped docker container with container id
    $ docker rm <containerid>

### Remove running docker container with container id
    $ docker rm -f <containerid>

### Remove the docker image with the docker image id
    $ docker rmi <imageid>

### Lists the details of all the network in the cluster
    $ docker network ls

### Login into docker hub
    $ docker login

### Save a new docker image with container id
    $ docker commit <containerid> <username>/<imagename>

### Upload a docker image with the image name
    $ docker push <username>/<imagename>

### History of a docker image with the image name
    $ docker history <imagename>

### Logs of the docker container with contained id
    $ docker logs <containerid>

### Create a volume which docker container will use to store data
    $ docker volume create

### Check volume
    $ docker volume ls
