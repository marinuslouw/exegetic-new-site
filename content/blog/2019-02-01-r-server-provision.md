---
title: "Provisioning an R Server"
author: Andrew Collier
date: 2019-02-01
draft: true
tags: ['R', 'AWS']
---

This post describes the process of provisioning an R server on AWS.

## EC2 Instance

Connect to AWS and spin up a suitable EC2 instance. You can probably get away with a `t3.micro`, but having a little more RAM in a `t3.small` or `t3.medium` will be handy. If you want to live large then go with a `t3.large`. Of course, there's a wide range of other options too.

A few notes:

- You can make things more cost effective by using a Spot Instance.
- Use the Ubuntu Server 18.04 LTS AMI.
- Make sure that the following ports are open: 20, 8787 and 3838.

## Connect & Swap

Once the instance is up, get the public IP and connect as the `ubuntu` user.

```bash
ssh ubuntu@3.85.89.116
```

Now [add some swap space](https://datawookie.netlify.com/blog/2015/06/amazon-ec2-adding-swap/). This will be especially important if you chose an instance with limited RAM.

## Create Users

You'll want to create some user accounts.

```bash
sudo adduser wookie
```

Provide a suitable password for the new account.

## R

We're just going to install the version of R which is included in the Ubuntu repositories. It's possible to get the most recent version of R, but that requires a little more work.

```bash
sudo apt-get update
sudo apt install r-base-core
```

It's handy to install some R packages which will be available to all users. We could install those from source, but there's also a [repository of prebuilt packages](https://launchpad.net/~marutter/+archive/ubuntu/c2d4u) maintained by Michael Rutter.

Add the [PPA](https://itsfoss.com/ppa-guide/) for the repository.

```bash
sudo add-apt-repository ppa:marutter/c2d4u
sudo apt-get update
```

Now install whatever packages are needed. For example, here are some essentials:

```bash
sudo apt install -y r-cran-dplyr r-cran-tidyr r-cran-shiny
```

## RStudio Server

Next we'll install RStudio Server.

Download and install the distribution

```bash
wget https://download2.rstudio.org/rstudio-server-1.1.463-amd64.deb
sudo dpkg -i rstudio-server-1.1.463-amd64.deb
```

You can test it out by visiting port 8787 in your browser. For example, if the instance has a public IP of 3.85.89.116 then go to http://3.85.89.116:8787.

## Shiny

Download and install the distribution.

```bash
wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.9.923-amd64.deb
sudo dpkg -i shiny-server-1.5.9.923-amd64.deb
```

You can test it out by visiting port 3838 in your browser. For example, if the instance has a public IP of 3.85.89.116 then go to http://3.85.89.116:3838.

New Shiny apps can be installed beneath `/srv/shiny-server/`.

## Wrapping Up

That's all that's required to create a provision a fairly complete R server including RStudio Server and Shiny Server.

There are a few tweaks that you can make to improve this setup:

- Install a more extensive range of packages.
- Create shared folders to enable collaboration.
- Create user groups to manage access to shared folders.
