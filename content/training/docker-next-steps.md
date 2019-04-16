---
title: "Docker: Next Steps"
topic: true
subjects: ['Docker']
draft: false
---

<!--
	More about layers: https://medium.com/@jessgreb01/digging-into-docker-layers-c22f948ed612
-->

This course builds on the [Docker: First Steps]({{< ref "docker-first-steps.md" >}}) course, introducing a selection of new topics which will take your Docker skills to the next level.

## Contents

- Dockerfile Revisited
	- Best practices
	- `ENV` - Default values for environment variables
- Debugging
	- Getting "inside" an image
	- `docker exec`
	- `docker attach`
- Volumes
	- Sharing data
	- Volumes on the host
	- Named volumes
- Networking
	- `docker network`
	- Network drivers
	- Bridge, Overlay and Host network
- Sharing Images
	- [Docker Hub](https://hub.docker.com/)
	- Docker Registry
	- `docker push` - publishing images
	- `docker search` - finding images
- Deploying
- Compose
	- Running multiple containers
	- Compose file syntax
	- Ports, volumes and links
	- Commands and flags
- Swarm
	- Distributing containers
	- Setup
	- Deploying application on a cluster

{{< comment >}}
- Kubernetes
	- Introduction

- Projects
	- Django/MySQL application using Docker Compose
{{< /comment >}}

## Prerequisites

In order for this course to make sense you should first complete the [Docker: First Steps]({{< ref "docker-first-steps.md" >}}) course.
