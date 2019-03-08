---
title: "Docker: First Steps"
topic: true
subjects: ['Docker']
draft: false
---

<!--
https://docs.docker.com/get-started/
https://thenewstack.io/understanding-the-docker-cache-for-faster-builds/
https://docker-curriculum.com/
https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b
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
	- `docker images` - list images
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
	- Layers and the Union File System
- Build Context
	- `.dockerignore`
- Projects
	- Static website
	- Dynamic webapp

## Prerequisites

Get set up for this course by creating an account on the following services:

- [AWS](http://aws.amazon.com/)
- [Docker Hub](https://hub.docker.com/)

Follow [these instructions](https://docs.docker.com/install/) to install Docker.
