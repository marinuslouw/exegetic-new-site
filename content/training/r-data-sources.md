---
title: "Data Sources"
topic: true
subjects: ['R']
subjects_weight: 21
draft: false
---

<!--
	- Data Types
  * Categorical
  * Continuous
  * Missing
  * Censored
- Gathering Data
  * Observational versus Experimental Data
  * Longitudinal Study
  * Cross-Sectional Study
- Data Sources
- Getting Data into R
  * CSV and other delimited files
    - Using `readr`
    - Writing to a delimited file
  * Spreadsheets
  * SQL
    - Accessing a Database from R
    - Using sqldf
- What are "tidy data"?
- Introduction to `dplyr`
  * `select()` and `rename()`
  * `filter()` and `slice()`
  * `arrange()`
  * `mutate()` and `transmute()`
  * `group_by()`
  * `summarise()`
  * `sample_n()` and `sample_frac()`
  * `distinct()`
  * Learning to love the `%>%` pipe: chaining operations
- Introduction to `tidyr`
  * `gather()`
  * `separate()` and `extract()`
  * `spread()`
- Storing Data in Native R Format
  * RDS
  * RData
  
 ## Resources
 
 - Hadley Wickham. [Tidy data](https://www.jstatsoft.org/index.php/jss/article/view/v059i10/v59i10.pdf). The Journal of Statistical Software, vol. 59, 2014.
-->

This course covers a range of options for getting data into R.

- Data from File
	- CSV using base and [readr](https://github.com/tidyverse/readr)
	- XLSX using [readxl](https://github.com/tidyverse/readxl)
	- JSON
- Relational Database
  - SQLite
  - MySQL
- Graph Database
  - [Neo4j](https://neo4j.com/) and [neo4r](https://github.com/neo4j-rstats/neo4r)

You'll also learn about options for exporting data from R.

- Data to File
  - CSV
  - XLSX using [writexl](https://github.com/ropensci/writexl)
  - JSON
  - RDS and RDA (native R formats)