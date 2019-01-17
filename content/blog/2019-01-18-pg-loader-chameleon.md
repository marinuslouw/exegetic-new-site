---
title: "PostgreSQL tools: PGLoader and PGChameleon"
author: Megan Beckett & Ian Rogers
date: 2019-01-17
draft: true
tags: ['postgresql', 'database', 'DBA', 'replication', 'mysql']
---

## Introduction

We recently explored some tools to help us migrate and replicate from a MySQL to PostgreSQL database. The reasons for why you might want to do such a task are varied, but for us, it had to do with a project where we needed to first copy one table from a MySQL to a PostgreSQL database, and then setup a continuous replication process to firstly have a copy, and therefore backup, on a separate server and then allow for further analyses between databases/schemas on the same server, of the same type.

This is fairly straightforward if your databases are the same system, but what if they are heterogeneous databases, like MySQL and PostgreSQL? Can we copy from one database to the other? Can we continuously replicate from a MySQL database to a PostgreSQL database?

In come two really useful tools that we discovered during our research:

- pgloader
- pg_chameleon

In this blog post we'll run through our basic set up and implementation, including a sandbox testing environment.

## pgloader

If in doubt, ask! And once again, I was really excited to make use of open source software, and even more so, engage with the developers. 

[Dimitri Fontaine](https://twitter.com/tapoueh) is a PostgreSQL guru and the founder of pgLoader. There is useful [documentation](https://pgloader.readthedocs.io/en/latest/), a white paper on the concept of [Continuous Migration](https://pgloader.io/white-paper/), and Dimitri himself is really active.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">If you&#39;re wanting to copy or migrate a <a href="https://twitter.com/hashtag/Database?src=hash&amp;ref_src=twsrc%5Etfw">#Database</a>, or specific tables, from <a href="https://twitter.com/hashtag/MySQL?src=hash&amp;ref_src=twsrc%5Etfw">#MySQL</a> to <a href="https://twitter.com/hashtag/PostgreSQL?src=hash&amp;ref_src=twsrc%5Etfw">#PostgreSQL</a>, this is such a handy tool from <a href="https://twitter.com/tapoueh?ref_src=twsrc%5Etfw">@tapoueh</a>: <a href="https://t.co/HMJMeVLq5H">https://t.co/HMJMeVLq5H</a></p>&mdash; Megan Beckett (@mbeckett_za) <a href="https://twitter.com/mbeckett_za/status/1069518233194151937?ref_src=twsrc%5Etfw">December 3, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

In summary, pgloader allows one to load data into PostgreSQL from various sources, such as:

- files (e.g. CSV, DBF, IXF)
- live databases 

pgloader has support for migrating the following RDBMS (Relationship Database Management system) in a fully automated way:

- DBF
- SQLite
- MySQL
- MS SQL Server

The documentation is excellent, but here's a quick recap of what we did.

### 1: Install pgloader

You can install pgloader directly from [apt.postgresql.org](apt.postgresql.org) and from official debian repositories, see [packages.debian.org/pgloader](packages.debian.org/pgloader).

{{< highlight r >}}
$ apt-get install pgloader
{{< /highlight >}}
You can also use a docker image - see details on Github repo.

### 2: Set up test databases

{{< highlight sql >}}
$ mysql -u root
> create database mysql_test;
> source mysql_test_data.sql
{{< /highlight >}}

{{< highlight sql >}}
$ psql postgres -U patrick
postgres=> CREATE DATABASE psql_test;
{{< /highlight >}}

### 3: Create a .load file
pgloader makes use of its own <i>Command Language</i> and there are two ways to do a migration, either:

- in a single command where you give a source for the data aand a PostgreSQL database connection target to load the data into; or
- use a .load command-file containing specifications in the pgloader <i>Command Language</i>.

{{< highlight r >}}
$ pgloader [<options>] SOURCE TARGET
$ pgloader [<options>] [<command-file>]
{{< /highlight >}}

I opted for the second option, as it was easier to build out and iterate.

Here's an example of `my_command.file.load`:

{{< highlight python >}}
LOAD DATABASE
     FROM      mysql://megan:<pwd>@localhost/mysql_test
     INTO postgresql://megan:<pwd>@localhost/psql_test

WITH include drop, create tables, create indexes, reset sequences,
      workers = 8, concurrency = 2,
      multiple readers per thread, rows per range = 25000

SET PostgreSQL PARAMETERS
      maintenance_work_mem to '128MB',
      work_mem to '12MB',
      search_path to 'vicidb, public'

SET MySQL PARAMETERS
      net_read_timeout  = '120',
      net_write_timeout = '120'

CAST type bigint to bigint drop typemod,
     type bigint when unsigned to bigint drop typemod,
     type datetime to timestamptz,
     type smallint to smallint drop typemod,
     type enum to enum

INCLUDING ONLY TABLE NAMES MATCHING 'my_special_table'

ALTER schema 'mysql_test' rename to 'public';

{{< /highlight >}}

#### WITH ...
There are several options here.

I specified `include drop` as then pgloader drops all the tables in the target PostgreSQL database whose names appear in the MySQL database. This option allows you to use the same command several times in a row until you figure out all the options, starting automatically from a clean environment. Very handy! You therefore also need the option to `create tables` each time.

Other options, such as `multiple readers per thread` and `concurrency` can help with performance. These are detailed in the documentation.

#### Casting considerations
This is probably one of the biggest benefits and features of pgloader - converting between different data types. pgloader has a number of defaults and you can specify your own casting rules. In my case, I found converting from MySQL `bigint` became numeric when unsigned, but wanted to keep as a PostgreSQL `bigint` and resolved this with the option:

{{< highlight python >}}
type bigint when unsigned to bigint drop typemod,
{{< /highlight >}}

I found [this](https://dev.mysql.com/doc/workbench/en/wb-migration-database-postgresql-typemapping.html) to be a useful resource on MySQL website to look at the mapping between MySQL and PostgreSQL datatypes.

#### Partial migration
We were interested in copying a single MySQL table into a PostgreSQL database and therefore made use of the partial migration to include only specific tables, as explained [here](https://pgloader.readthedocs.io/en/latest/ref/mysql.html#mysql-partial-migration), with the following line:

{{< highlight python >}}
INCLUDING ONLY TABLE NAMES MATCHING 'my_special_table'
{{< /highlight >}}

#### Alter schema to public

As described [here](https://github.com/dimitri/pgloader/issues/645), I also had to alter the schema and rename to 'public'.

{{< highlight python >}}
ALTER schema 'mysql_test' rename to 'public';
{{< /highlight >}}

### 4: Run your .load file

As specified before, execute your command file with the following:

{{< highlight r >}}
$ pgloader my_command_file.load
{{< /highlight >}}

If it fails, you'll get a very definitive `KABOOM!` in your terminal!

Another useful tip is to use the option `-- dry-run`. This allows testing a .load file without actually trying to load any data. It’s useful to debug it until it’s ok, in particular to fix connection strings.

And when it does work, it's very exciting! You'll get an output in your terminal, showing the result. For example, in my case, to copy a table with 8 million records from a MySQL to a PotgreSQL on a remote serve took about 6 minutes. 

So, we copied a table from MySQL to PostgreSQL (and pgload will definitely come into it's own hen migrating a whole database, which we didn't do here). but, what about a continuous replication from MySQL to PostgreSQL.

Step up pg_chameleon!

## pg_chameleon

Developed by [Federico Campoli](http://www.pgdba.org/), pg_chameleon has it's own Twitter account and following:

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/mysql?src=hash&amp;ref_src=twsrc%5Etfw">#mysql</a> to <a href="https://twitter.com/hashtag/postgresql?src=hash&amp;ref_src=twsrc%5Etfw">#postgresql</a> <a href="https://twitter.com/hashtag/replica?src=hash&amp;ref_src=twsrc%5Etfw">#replica</a> system <a href="https://twitter.com/hashtag/pgchameleon?src=hash&amp;ref_src=twsrc%5Etfw">#pgchameleon</a> new version 2.0.10 is out. read the instructions and upgrade!<a href="https://t.co/Z2zmDfMFDh">https://t.co/Z2zmDfMFDh</a></p>&mdash; pg_chameleon (@pg_chameleon) <a href="https://twitter.com/pg_chameleon/status/1035838871072735234?ref_src=twsrc%5Etfw">September 1, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

