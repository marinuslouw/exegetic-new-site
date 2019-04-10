---
title: "Web Scraping in R"
topic: true
subjects: ['R', 'Web Scraping']
subjects_weight: 130
---

During this course we'll scrape data from a number of sites including:

- postal codes from [GeoNames](http://www.geonames.org/);
- browser market share from [StatCounter](http://gs.statcounter.com/browser-market-share);
- weather data from [Weather Underground](https://www.wunderground.com/).

### Day 1

- Motivating Example <!-- Private Property -->
- Review of the Tidyverse
	- Highlights from [Data Wrangling]({{< ref "r-data-wrangling.md" >}})
- Introduction to Scraping
	- The components of an HTML document
	- Building a simple HTML document
	- DOM
	- CSS (summary of [CSS]({{< ref "web-css.md" >}}))
	- XPath (summary of [XPath]({{< ref "web-xpath.md" >}}))
	- Developer Tools
	- Important files: `robots.txt` and `sitemap.xml`
	- Ethics
- HTTP
	- How HTTP works
	- Diagnosing requests with `curl` and <https://httpbin.org/>
- Manual Scraping
	- Using [RCurl](https://cran.r-project.org/web/packages/RCurl/index.html) and [XML](https://cran.r-project.org/web/packages/XML/index.html).
- Scraping a Static Website using [rvest](https://github.com/hadley/rvest)
	- Retrieving page content
	- Navigation
	- Extracting text
	- Extracting attributes
	- Working with tables
	- Storing data as CSV or JSON.
	- Case Study
- Assisted Assignment <!-- IMDB -->

### Day 2

- Case Study <!-- drug tests using rvest -->
- Interacting with APIs
	- Using XHR to find an API
	- Building wrappers around APIs
- Dynamic Websites and JavaScript
	- Using [splashr](https://github.com/hrbrmstr/splashr) for JavaScript.
- Driving a Browser using [RSelenium](https://github.com/ropensci/RSelenium)
	- Why is RSelenium needed?
	- Navigation
	- Interacting with elements
	- Combining RSelenium with rvest
	- Useful JavaScript tools
	- Going headless
	- Case Study
- Building Robust Scrapers
	- Handling errors using `tryCatch()`
	- Functional tools from purrr: mapping, walking, `insistently()` and `slowly()`
- Deploying a Scraper in the Cloud
	- Launching and connecting to an EC2 instance
	- Headless browsers
	- Automation with cron