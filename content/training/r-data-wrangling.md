---
title: "Data Wrangling"
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

- Loading data from files
	- CSV using base and [readr](https://github.com/tidyverse/readr)
	- XLSX using [readxl](https://github.com/tidyverse/readxl)
	- JSON
- Manipulating Data Frames with [dplyr](https://github.com/tidyverse/dplyr)
	- Selecting columns with `select()`
	- Filtering rows with `filter()`
	- Sorting with `arrange()`
	- Adding and changing columns with `mutate()` and `transmute()`
	- Aggregation with `group_by()` and `summarise()`
	- Assorted other functions from dplyr
- Pivoting with [tidyr](https://github.com/tidyverse/tidyr)
	- Long versus wide data formats
	- Going wide with `spread()`
	- Getting long with `gather()`
	- Splitting compound columns using `separate()` and `extract()`
	- Explicit missing values with `complete()`
	- Handling columns of data frames with `nest()` and `unnest()`
- Functional programming with [purrr](https://github.com/tidyverse/purrr)
	- Mapping functions of a single variable with `map()`
	- Mapping to a specific data type
	- Mapping functions of two variables with `map2()`
	- Mapping functions with many variables using `pmap()`
	- Leveraging side effects with `walk()`, `walk2()` and `pwalk()`
	- Repeating with delays using `insistently()` and `slowly()`