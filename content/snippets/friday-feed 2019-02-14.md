---
title: "Dockter"
author: "Gerard Walsh"
date: '2019-02-08'
draft: yes
tags: ['friday-feed', 'R', 'Data Science']
---

## Context

Getting started with a new enviroment/programming language takes time. Just installing packages with the associated dependencies can be laborious and can further lengthen this process. When setting up R, packages are required to be compiled locally which can further result in an even lengthier _getting started_ process. Docker images are a great way to containerize and deploy software. One can download a Docker image, deploy it locally as a container and be up and running in a specific enviroment within minutes. However, building _your own_ Docker image to be deployed can be laborious. Changing or adding a single depedency can result in the entire image being rebuilt as well as the packages being redownloaded (unless you utilize the cache functionality - advanced). 

## Docker workflow

Let's continue with the case whereby we wanted to containerize a simple application. Building an ordinary docker image requires one to know what packages and associated dependencies are required. For instance, if we want to build an image that is capable of running R, our Dockerfile would start out with our `Dockerfile` looking something like:
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
where we should see an image that is named the same as the directory that we are working in: 
```
REPOSITORY                       TAG                         IMAGE ID            CREATED             SIZE
<directory-name>                      latest                      38604993d484        About an hour ago   916MB
```
Now, if we run our image as a container with:
```
$ docker run <directory-name> .
```
we are presented with a CLI whereby we can use R to evaluate scripts. But let's say we had a simple R script called `main.R` that loads the package `lubridate` and simply calls the function `now()` to give us the current date and time. So deploying our image as a container (a super useful piece of software to deploy, I know), would just result in the date and time printed to the CLI. Our `main.R` script would look like:
```
library(lubridate)
lubridate::now()
```
which we would need to include as a script in the directory we were working in, and build on our `Dockerfile` as follows:
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
The final line of our `Dockerfile` dictates that when the container is launched, it's default functionality is to run the script that we have specified (`main.R`) and the terminate the container. We would then proceed with building the image again:
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
after which we would build the image again and deploy it as previosly mentioned. However, making these changes to our Dockerfile is laborious and results in packages being re-downloaded and installed if they come after the line that we changed. This iterative process can take ages and can be rather frustrating. Thankfully, a more elegant solution does exist. 

## Dockter

This is where `dockter` comes in. [Dockter](https://github.com/stencila/dockter#roadmap) is a container image builder that generates a Dockerfile based off of your _source code_. Building a `.Dockerfile` off of your source code ensures an image contains every dependency and package required without any bloat - something that is quite hard to avoid when manually building an image. Calling (and noting the additional `t`):
```
$ dockter compile
```
generates a `.Dockerfile`, a `.DESCRIPTION` - a package description file for the required R packages, and a `.envrion.jsonld` - a JSON-LD document containing structure meta-data on your project and all of its dependencies. This makes life easy for us and allows us to truly containerize without having to experts in creating the enviroment for the package. Once we have called `dockter compile` we call:
```
dockter build 
```
whereby `dockter` reads the generated `.Dockerfile` and builds the image as standard. We can then deploy a container using the standard command `docker run <directory-name> .`. `Dockter` is not only designed to work with `R`, but other languages too such as `Python` - another package heavy language that can be frustrating to get to grips with. 

## CLosing thoughts

Docker is a great tool to save time getting an enviroment setup (think R or even Tensorflow-Python) and deploying standalone pieces of software. However, building an image can be laborious and even as time consuming as just performing a local system install - not to mention when trying to build a lightweight image. _Dockter_ makes this process much more simple and builds an image directly off of our source code, ensuring no depedencies are missed and our image is truly deployable. 