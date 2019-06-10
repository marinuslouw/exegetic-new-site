---
title: "Policy – Coding Standards"
subtitle: "Table of Contents"
draft: true
documents: ['Policy']
output:
  html_document:
    toc: true
---


Good coding style is like correct punctuation: you can manage without it, butitsuremakesthingseasiertoread. The standards below were taken from various sources. Please go through these and implement the coding standards of your relevant language. The aim of this document is to provide consistency across our various projects and undertakings. Following coding standards will make you, your colleagues, and every future version thereof, happier.


## __General__


### Source file encoding

- Use UTF-8 for all languages.


### Line length

- Line length is arbitrary.
- Whichever line length you prefer, keep it consistent across languages.
- Up to 120 characters are allowed.


### File header guidelines

- Use headers to add descriptions to your scripts.
- Start file headers on the 1st line of a script.
- File headers can be either a short introductory description, or a template.

```
# Script for automating notification sms'.
```
```
# =================================================================================================
# =                        Driver Performance - Notification events                               =
# =                                                                                               =
# =                            Megan Beckett <megan@exegetic.biz>                                 =
# =================================================================================================
```


### Section header guidelines

- Use headers to document and separate your code as it aids in the readability and interpretability of your code.

```
# LIBRARIES ----------------------------------------------------------------------------------------
```


### Commenting guidelines

- Comment your code wisely.
- It's a worthwhile investment.
- Don’t get carried away and comment every line of code - self-explanatory code should be left as is.
- Each line of a comment should begin with the relevant comment symbol and a single space.

```
# Load data from google drive.
```


### Architecture

Writing code without thinking of its architecture is useless in the same way as dreaming about your desires without a plan of achieving them. Think long-term about your intended code, for example.

- How it will be used.
- How it will be integrated into other services.
- What structure it will have.
- How it will be tested and debugged.
- How it will be updated.


### Package and module names 

- Packages (R) and modules (Python) should have short, all-lowercase names.
- The use of underscores are discouraged.


### Function, variable and object names

- Variable and function names should be lowercase.
- Use an underscore '_' to separate words within a name.
- Generally, variable names should be nouns and function names should be verbs.
- Strive for names that are concise and meaningful (this is not easy!).
- Avoid abbreviations and if you have to use them make sure they are commonly understood.

```
# Yes:
day_one
day_1
subscribers_geocode

# No:
first_day_of_the_month
DayOne
dayone
djm1
SubscribersGeocode
```


### Hard-coding

- The definition of hard-coding, is to fix data or parameters in a program in such a way that they cannot be altered without modifying the program.
- Get into a habit of not hard-coding.
- Code should be transferable.


### Duplication

- DRY - Don't Repeat Yourself.
- Duplication leads to unnecessary maintenance.
- If you are repeating your code, you likely need a function.


### Legibility

- Write clean, readable code.
- Use meaningful names and rather spend more than less time choosing a meaningful name.
- Follow convention: camelCase, underscore_case, PascalCase, etc.


## __Markdown__

Markdown's code policy section was compiled by taking liberally from loopback's [Markdown style guide](https://loopback.io/doc/en/contrib/Markdown-style-guide.html). Please visit the link for more guidelines and to further clarify the guidelines below.


### Indentation, headers and whitespaces

- Markdown files don't use extra indentation.
- Always insert an open line between a section heading and the section content.
- Always insert two blank lines in between sections.

### Links

- Always use absolute URLs, not relative URLs.

```
# Yes: 
[`automigrate.js`](https://github.com/strongloop/loopback-example-database/blob/postgresql/bin/automigrate.js).

# No: 
[`automigrate.js`](bin/automigrate.js).
```


## __R__

R's code policy section was compiled by taking liberally from Hadley's [Advanced R style guide](http://adv-r.had.co.nz/Style.html), the [tidyverse style guide](https://style.tidyverse.org/), and
Google's [R style guide](https://google.github.io/styleguide/Rguide.xml). Please visit the links for more guidelines and to further clarify the guidelines below.


### File names

- File names should be meaningful and end in '.R'.
- If files need to be run in sequence, prefix them with numbers.

```
0-download.R
1-parse.R
2-explore.R
```


### Spacing

- Place spaces around all infix operators (=, +, -, <-, etc.).
- The same rule applies when using '=' in function calls.
- Always put a space after a comma, and never before (just like in regular English).

```
# Yes:
average <- mean(feet / 12 + inches, na.rm = TRUE)

# No:
average<-mean(feet/12+inches,na.rm=TRUE)
```

For all the use cases of how to use spaces, go to the [syntax, spacing](http://adv-r.had.co.nz/Style.html) section of Hadley's (You know who Hadley is, right?) style guide.


### Curly braces

- An opening curly brace should never go on its own line and should always be followed by a new line.
- A closing curly brace should always go on its own line unless it’s followed by 'else'.
- Always indent the code inside curly braces.

```
if (y == 0) {
  log(x)
} else {
  y ^ x
}
```


### Assignment

- Use '<-', not '=', for assignment.

```
# Yes:
x <- 5

# No:
x = 5
```


### Line Breaks

- Variable name assignments take place on the same line.
- Insert a new line after every pipe (%>%).

```
# Yes:
subscribers <- fetch_subscribers()
subscribers <- subscribers %>% 
  select(date, customer_id, active, phone_number) %>% 
  arrange(date)

# No:
subscribers <- fetch_subscribers() %>% select(date, customer_id, active, phone_number) %>% arrange(date)
```


### Indentation

- Use two spaces for indentation.
- Never use tabs or mix tabs and spaces.
- The only exception is if a function definition runs over multiple lines.
- In that case, indent the second line to where the definition starts.

```
long_function_name <- function(a = "a long argument",
                               b = "another argument",
                               c = "another long argument") {
  # As usual code is indented by two spaces.
}
```



## __Python__

Python's code policy section was compiled by taking liberally from the PEP 8 [Python style guide](https://www.python.org/dev/peps/pep-0008/). Please visit the link for more guidelines and to further clarify the guidelines below.


### Line Breaks

- It is permissible to break before or after a binary operator, as long as the convention is consistent locally.
- For new code follow the style of traditional mathematics (break before binary operations)

```
# Yes: 
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```


### Blank lines

- Surround top-level function and class definitions with two blank lines.
- Method definitions inside a class are surrounded by a single blank line.


### Imports

- Imports are always put at the top of the file, just after any module comments and docstrings, and before module globals and constants.
- Imports should usually be on separate lines.
- Absolute imports are recommended.

```
# Yes: 
mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example

# No:  
import sys, os
```


### Class names

- Class names should normally use the CapWords convention.


### Type variable names

- Names of type variables introduced in PEP 484 should normally use CapWords preferring short names.
- 'T', 'AnyStr', 'Num'.
- It is recommended to add suffixes '_co' or '_contra' to the variables used to declare covariant or contravariant behaviour correspondingly.

```
from typing import TypeVar

VT_co = TypeVar('VT_co', covariant=True)
KT_contra = TypeVar('KT_contra', contravariant=True)
```


### Spacing

- Avoid extraneous whitespace.
- Avoid trailling whitespace.

```
# Yes: 
spam(ham[1], {eggs: 2})

# No:  
spam( ham[ 1 ], { eggs: 2 } )

# Yes: 
foo = (0,)

# No:  
bar = (0, )

# Yes:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

# No:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```


### Assignment

- Use '=' for assignment.


### Indentation

- Use four spaces for indentation.
- Tabs should be used solely to remain consistent with code that is already indented with tabs.
- Otherwise, only use spaces.
- Continuation lines should align wrapped elements either vertically, using Python's implicit line joining or using a hanging indent.
- When using a hanging indent, there should be no arguments on the first line and further indentation should be used to clearly distinguish itself as a continuation line.

```
# Add 4 spaces (an extra level of indentation) to distinguish arguments from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```

## __SQL__

SQL's code policy section was compiled by taking liberally from [Simon Holywell's style guide](https://www.sqlstyle.guide/) and [Firefox's SQL style guide](https://docs.telemetry.mozilla.org/concepts/sql_style.html#left-align-root-keywords). Please visit the links for more guidelines and to further clarify the guidelines below.


### General

- Use consistent and descriptive identifiers and names.
- Make use of white space and indentation to make code easier to read.
- Store ISO-8601 compliant time and date information (YYYY-MM-DD HH:MM:SS.SSSSS).
- Try to use only standard SQL functions instead of vendor specific functions for reasons of portability.
- Keep code succinct and devoid of redundant SQL, such as unnecessary quoting or parentheses or 'WHERE' clauses that can otherwise be derived.
- Include comments in SQL code where necessary.
- Precede comments with '--' and finish them with a new line.

```
-- Updating the file record after writing to the file
UPDATE 
  file_system
SET 
  file_modified_date = '1980-02-22 13:19:01.00000',
  file_size = 209732
 WHERE
  file_name = '.vimrc';
 ```

- Avoid CamelCase - it's difficult to scan quickly.
- Avoid descriptive prefixes or Hungarian notation such as 'sp_' or 'tbl'.
- Avoid plurals - use the more natural collective term where possible instead.


### Table naming conventions

- Use a collective name or, less ideally, a plural form.
- For example (in order of preference) staff and employees.
- Do not prefix with tbl or any other such descriptive prefix or Hungarian notation.
- Never give a table the same name as one of its columns and vice versa.
- Avoid, where possible, concatenating two table names together to create the name of a relationship table - rather than `cars_mechanics` use `services`.


### General naming conventions

- Ensure the name is unique and does not exist as a reserved keyword.
- Keep the length to a maximum of 30 bytes—in practice - this is 30 characters unless you are using multi-byte character set.
- Names must begin with a letter and may not end with an underscore.
- Only use letters, numbers and underscores in names.
- Avoid the use of multiple consecutive underscores — these can be hard to read.
- Avoid abbreviations and if you have to use them, make sure they are commonly understood.


### Line spacing and Indentation

- Keep all the commands left-alligned.
- Have each commmand on a new line for legibility.
- Don't include multiple arguments on one line.
- Have 'AND' or 'OR' on a single line.
- Indent 'AND' or 'OR'.

```
SELECT
  OrderInDriverID AS driver_id,
  UserName AS agent_name,
  Timestamp AS timestamp
FROM
  biWarehouse.dbo.DriverNotifications
WHERE
  timestamp >= @date_begin
  AND
  timestamp < @date_end
```
