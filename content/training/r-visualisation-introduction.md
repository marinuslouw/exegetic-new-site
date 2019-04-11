---
title: "Visualisation with ggplot2 and plotly"
subjects: ['R']
draft: false
---

In this course we'll introduce two packages for making visualisations with R: `ggplot2` (static plots and animations) and `plotly` (interactive plots).

## ggplot2

The [ggplot2](https://github.com/tidyverse/ggplot2) package has become the de facto standard for making plots in R. It's possible to quickly put together a simple plot for exploratory purposes. However, with a bit of effort such a plot can be transformed into a work of art.

- Introduction
	- Grammar of Graphics
- Example: Components of a plot
	- Data
	- Aesthetics
	- Layers
	- Facets
	- Theme
- Aesthetics
- Layers
	- Points
	- Lines
	- Box and Violin plots
	- Histogram, Density and Bar plots
	- Smooth
	- Stats versus Geoms
	- Position
- Facets
- Scales, Legends and Coordinates
- Themes
	- Builtin themes
	- Extra themes
	- Customising
- Animation

## plotly

<!-- https://plotly-book.cpsievert.me/ -->

[Plotly](https://github.com/ropensci/plotly) is an open source JavaScript library for creating interactive graphs and dashboards.

- Fundamentals
	- ggplot to plotly with `ggplotly()`
- Plot types
	- Scatter and Line plots
	- Box plots
	- Histogram and Bar plots
	- Heat maps and Contour plots
	- Polar plots
- Maps
- Combining plots
	- Sub-plots
	- Inset plots
	- Multiple axes
- Custom controls
- Dashboards
- Animation
- Exporting static images