---
title: "Docker: First Steps"
subjects: ['Docker']
draft: true
---

<!--
https://thenewstack.io/understanding-the-docker-cache-for-faster-builds/
https://docker-curriculum.com/
-->

## Course Description

- What is Docker?
	- Virtualisation
	- Docker versus VMWare and VirtualBox
	- Images and Containers
	- Daemon and Client
- Working with Images
	- Hello World - `busybox`
	- `docker pull` - fetch images
	- `docker images` - list fetched images
	- `docker run` - create a container
		- Naming a container (`--name`)
		- Handling cleanup (`--rm`)
		- Detach (`--detach`)
	- `docker logs` - output from containers
	- `docker ps` - list running containers
	- `docker stop` - stop running containers
	- `docker rm` - delete stopped containers
	- `docker rmi` - delete images we no longer need
- Building an Image
	- `docker pull` - build an image
	- Caching
	- Cleaning up temporary files
- Writing a Dockerfile
	- `FROM` - Specifying the base image
	- Tags
	- `COPY` - Copying things to the image
	- `ADD` - Another way to get stuff onto the image
	- `RUN` - Executing software on the image
	- `WORKDIR` - Setting the working directory
	- `EXPOSE` - What ports are available?
	- `CMD` - What will the image be running?
- Build Context
	- `.dockerignore`
- Sharing Images
	- [Dockerhub](https://hub.docker.com/)
	- `docker push` - publishing images
	- `docker search` - finding images
- Projects
	- Static website
	- Dynamic webapp
- Deploying

## Prerequisites

Get set up for this course by creating an account on the following services:

- [AWS](http://aws.amazon.com/)
- [Docker Hub](https://hub.docker.com/)

Follow [these instructions](https://docs.docker.com/install/) to install Docker.