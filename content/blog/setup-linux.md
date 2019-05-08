---
title: "R Setup – Linux"
date: 2019-01-01T03:00:00+02:00
draft: false
tags: ['R']
url: "/blog/r-setup-linux/"
description: "Setup instructions for R on a Linux system."
---

## R & RStudio Setup

These are instructions specific to Linux. Once you're finished installing R and RStudio, please go back to [R Setup – General]({{< ref "setup-general.md" >}}) to continue with the remaining installation.

Since you're on Linux, we'll assume you're comfortable with the terminal.

### Ubuntu

 1. Install R using

     ```
sudo apt-get update
sudo apt-get install r-base
```

2. Go to [Download RStudio](https://www.rstudio.com/products/rstudio/download/#download).
3. Under **Installers for Supported Platforms** select the appropriate *Ubuntu* version of the RStudio package.
4. Use `dpkg` to install the package. For example

    ```
sudo dpkg -i rstudio-1.2.1335-amd64.deb
```