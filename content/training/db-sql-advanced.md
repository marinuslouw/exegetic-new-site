---
title: "Intermediate SQL"
subjects: ['Database']
subjects_weight: 10
draft: true
---

## Course Description

### Data Query

Using SQL to execute queries against a Relational Database.

- Union
- Subqueries
	- `EXISTS`
	- `ANY` and `ALL`

### Data Definition

Using SQL to create the structure of a Relational Database.

- Normalisation
- Changing table structure with `ALTER`
	- Adding and removing columns
	- Adding a primary key
- Indexes
	- Adding an index
	- Examining indexes
- Renaming a table
- Views

### Data Manipulation

Using SQL to manipulate data in a Relational Database.

- Mixing `UPDATE` with `JOIN`

### Transaction Control

Using SQL transactions to ensure database integrity and process isolation.

- Why use transactions?
- Managing transactions
	- `COMMIT`
	- `SAVEPOINT`
	- `ROLLBACK`

### Optimising Queries

<!-- https://dev.mysql.com/doc/refman/5.5/en/execution-plan-information.html -->

- The query optimiser
- Generating a query plan with `EXPLAIN`
- Interpreting a query plan
- Writing better queries

### Users

- Creating users
- Access control with `GRANT` and `REVOKE`