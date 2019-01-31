---
title: "Introduction to Spark"
subjects: ['Spark']
draft: true
---

<!--
From our original DataCamp course.

Chapter 1 - Getting Started with Spark

* Lesson 1.1 - Connecting to Spark
        * A learning objective: Connect to Spark; create `SparkSession` and `SparkContext` objects; explore these objects.
        * Some functions introduced/used: `SparkSession` and `SparkContext`
* Lesson 1.2 - Unstructured Data
        * A learning objective: Create RDD manually; read unstructured data from file. Understand how data are distributed in Spark.
        * Some functions introduced/used: `parallelize()`, `textFile()` and `.getNumPartitions()`
* Lesson 1.3 - Structured Data
        * A learning objective: Convert RDDs to DataFrames; read structured data from file.
        * Some functions introduced/used: `.toDF()`, `createDataFrame()`, `read.csv()`, `read.json()` and `.count()`.

Chapter 2 - RDDs for Unstructured Data

* Lesson 2.1 - Getting to Grips with RDDs
        * A learning objective: Learn about actions. Perform simple actions on RDDs.
        * Some functions introduced/used: `.first()`, `.take()`, `.takeSample()` and `.collect()`
* Lesson 2.2 - Simple statistics
        * A learning objective: Generate simple statistics from RDDs. Getting quick approximate values.
        * Some functions introduced/used: `.min()`, `.max()`, `.sum()`, `.sumApprox()`, `.mean()`, `.meanApprox()`, `.sampleStdev()`, `.stdev()` and `.histogram()`
* Lesson 2.3 - Filtering
        * A learning objective: Filter specific data from a RDD.
        * Some functions introduced/used: `.filter()` and `.distinct()`
* Lesson 2.4 - Mapping
        * A learning objective: Apply function to transform a RDD.
        * Some functions introduced/used: `.map()` and `.flatMap()`

Chapter 3 - RDDs of Key-Value Pairs

* Lesson 3.1 - Creating a Pair RDD
        * A learning objective: Create a pair RDD.
        * Some functions introduced/used: `.map()`, `.keyBy()`, `.keys()` and `.values()`
* Lesson 3.2 - Transformations on a Pair RDD
        * A learning objective: Apply function to transform values in a pair RDD.
        * Some functions introduced/used: `.mapValues()` and `.flatMapValues()`
* Lesson 3.3 - Summarising by Key
        * A learning objective: Generate grouped summary data.
        * Some functions introduced/used: `.countByKey()`, `.reduceByKey()` and `.sortByKey()`
* Lesson 3.4 - Persistence
        * A learning objective: Improve efficiency by persisting intermediate results.
        * Some functions introduced/used: `.cache()`, `.persist()` and `.unpersist()`

Chapter 4 - DataFrames for Structured Data

* Lesson 4.1 - Choosing Rows and Columns
        * A learning objective: Extract subsets of data from a DataFrame; DataFrame attributes.
        * Some functions introduced/used: `.select()`, `.drop()` and `.filter()`
* Lesson 4.2 - Merging and Aggregation
        * A learning objective: Merge data from multiple DataFrame objects. Generate aggregate results.
        * Some functions introduced/used: `.join()`, `.groupBy()`
* Lesson 4.3 - SQL
        * A learning objective: Manipulate data using Spark SQL.
        * Some functions introduced/used: `sql()`
* Lesson 4.4 - Playing with Partitions
        * A learning objective: Change the way that data are partitioned across the cluster.
        * Some functions introduced/used: `.getNumPartitions()`, `.coalesce` and `.repartition()`
-->