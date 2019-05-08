---
title: "R Setup – General"
date: 2019-01-01T00:00:00+02:00
draft: true
tags: ['R']
url: "/blog/setup-general/"
description: "How to get your system set up for use in our R training."
---

Below are the setup instructions for the various bits of software we use in our training courses.

Further instructions for specific platforms can be found at the following pages:

- [Windows]({{< ref "setup-windows.md" >}})
- [Mac]({{< ref "setup-mac.md" >}}) and
- [Linux]({{< ref "setup-linux.md" >}}).


## R and RStudio Setup

### Install R

Install a [recent version of R](https://cloud.r-project.org/). We recommend a version >= R 3.5.1 "Feather Spray".

{{< highlight r >}}
> getRversion()
[1] ‘3.5.1’
{{< /highlight >}}

### Install RStudio

Install a [recent version of RStudio](https://www.rstudio.com/products/rstudio/download/#download). We recommend a version >= RStudio 1.1.463.

## R Packages

### Update Existing R Packages

Update all installed packages using either

{{< highlight r >}}
> update.packages(ask = FALSE, checkBuilt = TRUE)
{{< /highlight >}}

or

{{< highlight r >}}
> devtools::upgrade_packages(TRUE)
{{< /highlight >}}

### Install Essential R Packages

There are some packages that we'll always use. Make sure you have those installed.

{{< highlight r >}}
> install.packages("tidyverse")
{{< /highlight >}}

### Install Other R Packages

Install other packages from CRAN.

{{< highlight r >}}
> install.packages("flexdashboard")
> install.packages("learnr")
> install.packages("bookdown")
{{< /highlight >}}

Install a few packages directly from GitHub.

{{< highlight r >}}
> devtools::install_github('rstudio/blogdown', dependencies = TRUE, upgrade = "always")
> devtools::install_github('yihui/xaringan', dependencies = TRUE, upgrade = "always")
{{< /highlight >}}

### Hugo

Check installed version of Hugo.

{{< highlight r >}}
> blogdown::hugo_version()
{{< /highlight >}}

If Hugo was not found on your system then install using

{{< highlight r >}}
> blogdown::install_hugo()
{{< /highlight >}}

If the version is old (< 0.52) then update.

{{< highlight r >}}
> blogdown::update_hugo()
{{< /highlight >}}

{{< comment >}}
## Git

<!-- https://arm.rbind.io/prework/github/ -->
{{< /comment >}}
