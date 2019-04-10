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

Docker is a tool which makes it easier to create, deploy and run applications using containers. A container encapsulates a complete execution environment. As a result the container can be run on any hardware or operating system that supports Docker.

This course will teach you everything that you need to know to start using Docker.

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
- Writing a Dockerfile
	- `FROM` - Specifying the base image
	- Tags
	- `COPY` - Copying things to the image
	- `ADD` - Another way to get stuff onto the image
	- `RUN` - Executing processes on the image
		- Using `apt` to add software
		- Asserting non-interactive mode
	- `WORKDIR` - Setting the working directory
	- `EXPOSE` - What ports are available?
	- `CMD` - What will the image be running?
	- Layers and the Union File System
- Building an Image
	- `docker build` - build an image
	- Caching
	- Cleaning up temporary files
	- The build context and `.dockerignore`

<!--
- Projects
	- Static website
	- Dynamic webapp
-->

## Prerequisites

1. Follow [these instructions](https://docs.docker.com/install/) to install Docker.
2. Create accounts on the following services:

- [AWS](http://aws.amazon.com/) and
- [Docker Hub](https://hub.docker.com/).

3. The [UNIX Essentials]({{< relref "unix-essentials.md" >}}) course is useful for understanding some of the details of a Dockerfile.
