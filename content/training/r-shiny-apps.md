---
title: "Shiny: Building Interactive Data-Driven Apps"
subjects: ['R']
subjects_weight: 120
draft: false
---

<!--
https://www.londonr.org/wp-content/uploads/sites/2/presentations/LondonR_-_Workshop-Introduction_to_Shiny_-_Aimee_Gott_-_20150330.pdf
https://uomresearchit.github.io/RSE18-shiny-workshop/
https://github.com/rstudio/webinars/tree/master/47-introduction-to-shiny
https://github.com/juliasilge/intro_to_shiny
https://github.com/Robinlovelace/learning-shiny
https://shiny.rstudio.com/tutorial/
https://deanattali.com/blog/building-shiny-apps-tutorial/
https://github.com/rstudio-education/intro-shiny-rmarkdown
https://shiny.rstudio.com/articles/debugging.html
-->

Shiny is a package for building interactive web apps with R. The apps can be hosted as standalone webpages or embedded in a markdown document.

- What is Shiny?
  - Samples from App Gallery
- Components of a Shiny app
  - Simple example
- User Interface (UI)
  - Layouts
  - HTML formatting
  - Input controls
  - Panels and tabsets
- Server
  - Rendering output
  - Plots
  - Tables
  - `uiOutput()` for dynamic UI elements
- Reactivity
  - `reactive()`
  - `isolate()`
  - `eventReactive()`
  - `reactiveValues()`
- Debugging
- Enhancements
  - CSS
  - Shiny themes
  - HTML widgets
  - Javascript
- Deploying
  - [shinyapps.io](https://www.shinyapps.io/)
  - Shiny Server
- Scaling Shiny
  - [Shinyproxy](https://www.shinyproxy.io/)

## Setup

```
install.packages(c("shiny", "rmarkdown", "DT", "devtools", "flexdashboard",
                   "gapminder", "rticles", "shinydashboard", "shinythemes", 
                   "tidyverse", "tufte", "xaringan"),
                 repos = "http://cran.rstudio.com")
```
