---
title: "Dockter"
author: "Gerard Walsh"
date: '2019-02-08'
draft: yes
tags: ['friday-feed', 'R', 'Data Science']
---

## Context

Getting started with a new programming language and environment takes time. The first step of installing the required packages, with the associated dependencies, can be laborious and can further lengthen this process. When setting up R, packages are required to be compiled locally which can result further in an _even lengthier_ getting started process. [Docker](https://www.docker.com/why-docker) images are a great way to containerize and deploy software. One can download a Docker image, deploy it locally as a container and be up and running in a specific environment within minutes. However, building _your own_ Docker image to be deployed can be laborious too. Changing or adding a single dependency can result in the entire image being rebuilt as well as the packages required for the image being re-downloaded (unless you utilize the cache functionality - advanced). 
  
## Docker workflow

Let's discuss the case whereby we wanted to containerize a simple application. Building an ordinary Docker image requires one to know what packages and associated dependencies are required. For instance, if we want to build an image that is capable of running R, our Dockerfile would start out looking something like:
```
# Base image
FROM ubuntu:18.04

RUN apt-get update \
 && apt-get install -y \
      apt-transport-https \
      ca-certificates \
      curl \
      git \
      r-base \ # Important!!!
      software-properties-common
      
# This tells Docker the default command to run when the container is started
CMD bash
```
Great, now we have an R base image in Ubuntu 18.04 which we can build with:
```
$ docker build .
``` 
after which we can list our availabe images with: 
```
$ docker image ls
```
where we should see an image name that corresponds to the directory that we are working in.
```
REPOSITORY                       TAG                         IMAGE ID            CREATED             SIZE
<directory-name>                      latest                      38604993d484        About an hour ago   916MB
```
Now, if we run our image as a container with:
```
$ docker run <directory-name> .
```
we are presented with a CLI which we can use R to evaluate scripts. But let's say we had a simple R script called `main.R` that loads the package `lubridate` and simply calls the function `now()` to give us the current date and time. So deploying our image as a container (a super useful piece of software to deploy, I know), would just result in the date and time printed to the CLI. Our `main.R` script would look like:
```
library(lubridate)
lubridate::now()
```
which we would need to include as a script in the directory we were working in. To build our new image, we would modify our `Dockerfile` as follows:
```
# Base image
FROM ubuntu:18.04

RUN apt-get update \
 && apt-get install -y \
      apt-transport-https \
      ca-certificates \
      curl \
      git \
      r-base \ # Important!!!
      software-properties-common
      
#Copies the script from our working directory on the host into the image we are building
COPY main.R main.R
      
# This dictates the default command to run when the container is started
CMD Rscript main.R
```
The final line of our `Dockerfile` dictates that when the container is launched, it's default functionality is to run the script that we have specified (`main.R`) and then terminate the container. We would then proceed with building the image again:
```
$ docker build .
``` 
and after which we would deploy a container with:
```
$ docker run <directory-name> .
```
which would result in:
```
Error in library(lubridate) : there is no package called ‘lubridate’
```
So we need to install the package `lubridate` which we can do either by installing it via CLI (in the container) or build it into the image with an `install_script.R` (more attractive). Our `Dockerfile` would then look something like:
```
# Base image
FROM ubuntu:18.04

RUN apt-get update \
 && apt-get install -y \
      apt-transport-https \
      ca-certificates \
      curl \
      git \
      r-base \ # Important!!!
      software-properties-common
      
#Copies the script from our working directory on the host into the image we are building
COPY main.R main.R

#Copies the install script from our working directory on the host into the image we are building
COPY install_script.R install_script.R

# install the package into base R
RUN Rscript install_script.R

# The default functionality
CMD Rscript main.R
```
We would proceed to build the image again and deploy it as previously mentioned. However, making these changes to our Dockerfile is laborious and can also result in packages being re-downloaded and re-installed upon each image build. This iterative process can take ages and can be rather frustrating. Thankfully, a more elegant solution does exist. 

## Dockter

This is where `dockter` comes in. [Dockter](https://github.com/stencila/dockter#roadmap) is a container image builder that generates a Dockerfile based off of your _source code_. Building a Dockerfile off of your source code ensures an image contains every dependency and package required without any bloat - something that is quite hard to avoid when manually building an image. Calling (and noting the additional `t`):
```
$ dockter compile
```
generates a `.Dockerfile` (notice the prefix), a `.DESCRIPTION` (a package description file for the required R packages) and a `.envrion.jsonld` (a JSON-LD document containing structure meta-data on your project and all of its dependencies). It should be noted that these files are invisible and but can be viewed with `ctrl+h` (in Ubuntu). _Dockter_ makes our lives easier and allows us to truly containerize without having to be experts in creating the environment for the package. Once we have called `dockter compile` we call:
```
dockter build 
```
whereby `dockter` reads the generated `.Dockerfile` and builds the image as usual. We can then deploy a container using the standard command `docker run <directory-name> .`. `Dockter` is not only designed to work with `R` but other languages too such as `Python` - another package heavy language that can be frustrating to get to grips with. 

## Closing thoughts

Docker is a great tool to save time when getting an environment setup (think R or even Tensorflow-Python) and deploying standalone pieces of software. However, building an image can be laborious and as time-consuming as just performing a local system install - not to mention when trying to build a lightweight image. _Dockter_ makes this process much more simple and builds an image directly off of our source code, ensuring no dependencies are missed and that our image is able to be deployed. 