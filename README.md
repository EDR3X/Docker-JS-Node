# Command Cheatsheet

## Demo Dockerfile

```Dockerfile
FROM node:17-alpine

RUN npm install -g nodemon

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 4000

CMD ["npm", "run", "dev"]

```

### Details of Dockerfile

> `FROM node:17-alpine` imports node version 17 on alpine linux
>
> `RUN npm install -g nodemon` installs nodemon as global dependency on specified platform above
>
> `WORKDIR /app` specifies directory on a container
>
> `COPY package.json .` copies package.json to that particular directory on container
>
> `RUN npm install` installs all other dependencies present in package.json
>
> `COPY . .` copies all file form workind directory to container directory i.e. /app
>
> `EXPOSE 4000` exposes port of a container
>
> `CMD ["npm", "run", "dev"]` start the script from package.json

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

# docker-compose.yaml

## Demo docker-compose.yaml file

```yaml
version: "3.8"
services:
  api:
    build: ./api
    container_name: api_c
    ports:
      - "4000:4000"
    volumes:
      - ./api:/app
      - ./app/node_modules
```

> `build:` requires relative path to the DockerFile
>
> `container:` requires name of container to save to
>
> `ports:` requires multiple ports to map system and container's port
>
> `volumes:` requires list of volumes that maps system's folder to container i.e. form above we can say that `./api` is mapped to `/app` of a container, `./app/node_modules` is there so that it won't get deleted every time the file changes.

## Commands to run/stop docker-compose.yaml file

`docker-compose up` > runs docker-compose.yaml file

`docker-compose down` > stops docker-compose.yaml file and only removes container

`docker-compose down --rmi all -v` > stops docker-compose.yaml and deletes all Image, Container and Volume
