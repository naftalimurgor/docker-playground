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


# Legacy  build is DEPRECATED
use builderx:
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/


The warning you received indicates that the legacy builder in Docker is deprecated and will be removed in a future release. To address this, Docker suggests using BuildKit, which is a modern build system for Docker images. You can use the `buildx` component to build Docker images with BuildKit.

Here are the steps to set up and use `buildx` with Docker:

1. Install Docker CLI with `buildx`:
   - Ensure you have Docker installed on your system. If you don't have Docker, you can download and install it from the official Docker website.

2. Install `buildx` by running the following command:
   ```bash
   docker buildx create --use
   ```

3. Verify that `buildx` is properly set up by running:
   ```bash
   docker buildx version
   ```

4. You can now use `docker buildx` to build your Docker images. Modify your Dockerfile as needed.

5. Build your Docker image using `docker buildx`:
   ```bash
   docker buildx build -t your-image-name:your-tag .
   ```
   Replace `your-image-name` and `your-tag` with your desired image name and tag.

This will build your Docker image using BuildKit with `docker buildx`. BuildKit offers several advantages, including improved performance and better support for advanced features like cache and multi-platform builds.

Using BuildKit with `buildx` is the recommended way to build Docker images, as it is the modern approach and will eventually replace the legacy builder.