# Build commands

## Building a Image

`docker build -t myImage .`

> `myImage` is name of a image we just created

`docker build -t myImage:v1` -> **To build image with a tag**

> here `myImage` is created with tag `v1`

## Building a Container

`docker run --name myImage_c -p 5000:5000 --rm myImage:v1`

> Container is created with name `myImage_c` and is mapped to port `5000` of system to port `5000` of container on `myImage:v1` Image > `--rm` deletes the container after it is closed.

## Seeing Images and Containers

`docker images` > lists out all images present in a system.

`docker ps` > lists out all container processes
