---
title: "Data Manipulation in the Tidyverse"
subjects: ['R']
draft: true
---

- Compound Data Structures
	- Vectors
	- Lists
	- Data Frames
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