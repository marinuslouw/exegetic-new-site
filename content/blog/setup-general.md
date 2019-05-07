---
title: "Setup: General"
date: 2019-01-01T00:00:00+02:00
draft: true
tags: ['R', 'Python']
url: "/blog/setup-general/"
description: "How to get your system set up for use in our training."
---

Below are the setup instructions for the various bits of software we use in our training courses.

Further instructions for specific platforms can be found at the following pages:

- [Windows]({{< ref "setup-windows.md" >}})
- [Mac]({{< ref "setup-mac.md" >}}) and
- [Linux]({{< ref "setup-linux.md" >}}).

## Install R

Install a [recent version of R](https://cloud.r-project.org/). We recommend a version >= R 3.6.0 "Planting of a Tree".

{{< highlight r >}}
> getRversion()
[1] ‘3.6.0’
{{< /highlight >}}

## Install RStudio

Install a [recent version of RStudio](https://www.rstudio.com/products/rstudio/download/#download). We recommend a version >= RStudio 1.2.1335.

## R Packages

#### Update Existing R Packages

Update all of your installed packages.

{{< highlight r >}}
> update.packages(ask = FALSE, checkBuilt = TRUE)
# or
> devtools::upgrade_packages(TRUE)
{{< /highlight >}}

#### Install Essential R Packages

There are some packages that we'll always use. Make sure you have those installed.

{{< highlight r >}}
> install.packages("tidyverse")
{{< /highlight >}}

#### Install Other R Packages

Install some other packages from CRAN.

{{< highlight r >}}
> install.packages("flexdashboard")
> install.packages("learnr")
> install.packages("bookdown")
{{< /highlight >}}

Install other packages directly from GitHub.

{{< highlight r >}}
> devtools::install_github('rstudio/blogdown', dependencies = TRUE, upgrade = "always")
> devtools::install_github('yihui/xaringan', dependencies = TRUE, upgrade = "always")
{{< /highlight >}}

## Git

<!-- https://arm.rbind.io/prework/github/ -->