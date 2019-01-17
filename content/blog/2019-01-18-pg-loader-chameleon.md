---
title: "PostgreSQL tools: PGLoader and PGChameleon"
author: Megan Beckett & Ian Rogers
date: 2019-01-17
draft: true
tags: ['postgresql', 'database', 'DBA', 'replication', 'mysql']
---

## Introduction

We recently explored some tools to help us migrate and replicate from a MySQL to PostgreSQL database. The reasons for why you might want to do such a task are varied, but for us, it had to do with a project where we needed to first copy one table from a MySQL to a PostgreSQL database, and then setup a continuous replication process to have a copy on a separate server and allow for further analyses between databases/schemas on the same server, of the same type.

This is fairly straightforward if your databases are the same system, but what if they are heterogeneous databases, like MySQL and PostgreSQL? Can we copy from one database to the other? Can we continuously replicate from a MySQL database to a PostgreSQL database?

In come two really useful tools that we discovered during our research:

- pgloader
- pg_chameleon

In this blog post we'll run through our basic set up and implementation, including a sandbox testing environment.

## pgloader

If in doubt, ask! And once again, I was really excited to make use of opensource software, and even more so, engage with the developers. 

[Dimitri Fontaine](https://twitter.com/tapoueh) is a PostgreSQL guru and the founder of pgLoader.  

There is useful [documentation](https://pgloader.readthedocs.io/en/latest/), a white paper on the concept of [Continuous Migration](https://pgloader.io/white-paper/), and Dimitri himself is really active.

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

We were interested in copying a single MySQL table into a postgreSQL database and therefore made use of the partial migration to include only specific tables, as explained (here)[https://pgloader.readthedocs.io/en/latest/ref/mysql.html#mysql-partial-migration].

### Step 1: Install pgloader



### Alter schema to public

As described (here)[https://github.com/dimitri/pgloader/issues/645], I also had to alter the schema and rename to 'public'.

### Casting considerations





## pg_chameleon

Developed by (Federico Campoli)[http://www.pgdba.org/], pg_chameleon has it's own Twitter account and following:

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/mysql?src=hash&amp;ref_src=twsrc%5Etfw">#mysql</a> to <a href="https://twitter.com/hashtag/postgresql?src=hash&amp;ref_src=twsrc%5Etfw">#postgresql</a> <a href="https://twitter.com/hashtag/replica?src=hash&amp;ref_src=twsrc%5Etfw">#replica</a> system <a href="https://twitter.com/hashtag/pgchameleon?src=hash&amp;ref_src=twsrc%5Etfw">#pgchameleon</a> new version 2.0.10 is out. read the instructions and upgrade!<a href="https://t.co/Z2zmDfMFDh">https://t.co/Z2zmDfMFDh</a></p>&mdash; pg_chameleon (@pg_chameleon) <a href="https://twitter.com/pg_chameleon/status/1035838871072735234?ref_src=twsrc%5Etfw">September 1, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


{{< highlight r >}}
# Some R code goes here.
x <- 1
{{< /highlight >}}

## Another Heading

More text.