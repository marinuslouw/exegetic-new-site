---
title: "Web Scraping"
subjects: ['R', 'Web Scraping']
subjects_weight: 130
---

### Day 1

- Motivating Example <!-- Private Property -->
- Review of the Tidyverse
	- Highlights from [Data Manipulation in the Tidyverse]({{< ref "r-data-manipulation.md" >}})
- Introduction to Scraping
	- DOM
	- Developer Tools
	- CSS (summary of [CSS]({{< ref "web-css.md" >}}))
	- XPath (summary of [XPath]({{< ref "web-xpath.md" >}}))
	- Important files: `robots.txt` and `sitemap.xml`
	- Ethics
- HTTP
	- How HTTP works
	- Diagnosing requests with `curl` and <https://httpbin.org/>
- Scraping a Static Website using [rvest](https://github.com/hadley/rvest)
	- Retrieving page content
	- Navigation
	- Extracting text
	- Extracting attributes
	- Working with tables
	- Case Study
- Assisted Assignment <!-- IMDB -->

### Day 2

- Case Study <!-- drug tests using rvest -->
- Interacting with APIs
	- Using XHR to find an API
	- Building wrappers around APIs
- Scraping a Dynamic Website using [RSelenium](https://github.com/ropensci/RSelenium)
	- Why is RSelenium needed?
	- Navigation
	- Interacting with elements
	- Combining RSelenium with rvest
	- Useful JavaScript tools
	- Case Study
- Building Robust Scrapers
	- Handling errors using `tryCatch()`
	- Functional tools from purrr: mapping, walking, `insistently()` and `slowly()`
- Deploying a Scraper in the Cloud
	- Launching and connecting to an EC2 instance
	- Headless browsers
	- Automation with cron