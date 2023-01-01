# docker-playground

## Overview

- Build and run an image as a container
- Share images using Docker Hub
- Deploy Docker applications using multiple containers with a database
- eRun applications using Docker Compose

### What is a container?

is a runnable instance of an image. You can create, start, stop, move, or delete a container using the DockerAPI or CLI.
can be run on local machines, virtual machines or deployed to the cloud.

is portable (can be run on any OS).
is isolated from other containers and runs its own software, binaries, and configurations.

## Dockerize app
```# syntax=docker/dockerfile:1
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

## Build application
`docker build . -t <tag-image>`
```bash
docker build . -t naftalimurgor/app
```

## Run application(container)
`docker run -dp <host port>:<container port> image/tag`
```bash
docker run -dp 3000:3000 naftalimurgor/app
```

## Stop container
`docker ps`

`docker stop <image-id>`

## Delete image

`docker images`: List images

To delete: `docker rmi -f <image-name>`