# Command Cheatsheet

## Building a Image

`docker build -t myImage .`

> `myImage` is name of a image we just created

`docker build -t myImage:v1 .`

> here `myImage` is created with tag `v1`

## Building a Container

`docker run --name myImage_c -p 5000:5000 myImage:v1`

> Container is created with name `myImage_c` and is mapped to port `5000` of system to port `5000` of container on `myImage:v1` Image. `--rm` can be added between port number and imageName so that container is deleted after it stops running

## Starting, Closing and listing Containers

`docker start myContainer` > starts myContainer named container which is already created

`docker images` > lists out all images present in a system.

`docker ps` > lists out all currently running containers

`docker ps -a` > lists out all containers on a system

`docker stop myContainer` > stops running container named myContainer

## Removing/Deleting existing containers/images

`docker image rm myImage`

> Removes image named `myImage`, we can add `-f` at end to forcefully delete the image.

`docker container rm myContainer`

> Removes container named `myContainer`, we can many other containers at last to remove multiple containers at once.

`docker system prune -a`

> **Very Dangerous Command** this permanently removes all containers and images in a system
