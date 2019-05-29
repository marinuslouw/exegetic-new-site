---
title: "Policy – Coding Standards"
draft: true
documents: ['Policy']
---

Good coding style is like correct punctuation: you can manage without it, butitsuremakesthingseasiertoread. The standards below were taken from various sources. Please go through these and implement the coding standards of your relevant language. The aim of this document is to provide consistency across our various projects and undertakings. Following coding standards will make you, your colleagues, and every future version thereof, happier.

## General

### Commenting guidelines
- Comment your code wisely.
- It's a worthwhile investment.
- Don’t get carried away and comment every line of code!
- Obvious code should be left as is.

### Architecture
Writing code without thinking of its architecture is useless in the same way as dreaming about your desires without a plan of achieving them.

- Before you start, think long-term about your intended code:
- how it will be used,
- how it will be integrated into other services,
- what structure it will have,
- how it will be tested and debugged,
- and how it will be updated.

### Hard-coding
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

## R

R's code policy section was compiled by taking liberally from Hadley's [Advanced R style guide](http://adv-r.had.co.nz/Style.html), the [tidyverse style guide](https://style.tidyverse.org/), and
Google's [R style guide](https://google.github.io/styleguide/Rguide.xml). Please visit the links for more guidelines and to further clarify the guidelines below.

### Line length
- Strive to limit your code to 100 characters per line.
- In R, you can set this margin by going to: tools > global options > code > display > margin column > 100

### Header guidelines
- Use headers to document and separate your code.
- It aids in the readability and interpretability of your code.
```
# LIBRARIES ----------------------------------------------------------------------------------------
```

### Commenting guidelines
- Comment your code.
- Each line of a comment should begin with the comment symbol and a single space: #
- Comments should explain the why, not the what.
```
# Load data from google drive.
```

### File names
- File names should be meaningful and end in .R.
- If files need to be run in sequence, prefix them with numbers.
```
0-download.R
1-parse.R
2-explore.R
```

### Object names
- Variable and function names should be lowercase.
- Use an underscore (_) to separate words within a name.
- Generally, variable names should be nouns and function names should be verbs.
- Strive for names that are concise and meaningful (this is not easy!).
```
# Good
day_one
day_1

# Bad
first_day_of_the_month
DayOne
dayone
djm1
```

### Spacing
- Place spaces around all infix operators (=, +, -, <-, etc.).
- The same rule applies when using = in function calls.
- Always put a space after a comma, and never before (just like in regular English).
```
# Good
average <- mean(feet / 12 + inches, na.rm = TRUE)

# Bad
average<-mean(feet/12+inches,na.rm=TRUE)
```

For all the use cases of how to use spaces, go to the [syntax, spacing](http://adv-r.had.co.nz/Style.html) section of Hadley's (You know who Hadley is, right?) style guide.

### Curly braces
- An opening curly brace should never go on its own line and should always be followed by a new line.
- A closing curly brace should always go on its own line unless it’s followed by else.
- Always indent the code inside curly braces.
```
if (y == 0) {
  log(x)
} else {
  y ^ x
}
```

### Assignment
- Use <-, not =, for assignment.
```
# Good
x <- 5
# Bad
x = 5
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

## Python

Python's code policy section was compiled by taking liberally from the PEP 8 [Python style guide](https://www.python.org/dev/peps/pep-0008/). Please visit the link for more guidelines and to further clarify the guidelines below.

### Line length
- Strive to limit the line length to a maximum of 79 characters.
- Up to 99 characters are allowed.

### Line Breaks
- It is permissible to break before or after a binary operator, as long as the convention is consistent locally.
- For new code follow the style of traditional mathematics (break before binary operations)
```
# Yes: easy to match operators with operands
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

### Blank lines
- Surround top-level function and class definitions with two blank lines.
- Method definitions inside a class are surrounded by a single blank line.

### Source file encoding
- Code in the core Python distribution should always use UTF-8 (or ASCII in Python 2).
- Files using ASCII (in Python 2) or UTF-8 (in Python 3) should not have an encoding declaration.

### Imports
- Imports are always put at the top of the file, just after any module comments and docstrings, and before module globals and constants.
- Imports should usually be on separate lines.
- Absolute imports are recommended.
```
Yes: mypkg.sibling
     from mypkg import sibling
     from mypkg.sibling import example

No:  import sys, os
```

### Header guidelines
- Use headers to document and separate your code.
- It aids in the readability and interpretability of your code.
```
Placeholder
```

### Commenting guidelines
- Comment your code.
- Each line of a comment should .................
- Comments should explain the why, not the what.
```
Placeholder
```
### Package ad module names
- Modules should have short, all-lowercase names.
- Underscores can be used in the module name if it improves readability.
- Python packages should also have short, all-lowercase names, although the use of underscores are discouraged.

### Class names
- Class names should normally use the CapWords convention.

### Type variable names
- Names of type variables introduced in PEP 484 should normally use CapWords preferring short names.
- T, AnyStr, Num.
- It is recommended to add suffixes _co or _contra to the variables used to declare covariant or contravariant behaviour correspondingly.
```
from typing import TypeVar

VT_co = TypeVar('VT_co', covariant=True)
KT_contra = TypeVar('KT_contra', contravariant=True)
```

### Function and variable names
- Function names should be lowercase, with words separated by underscores as necessary to improve readability.
- Variable names follow the same convention as function names.

### Spacing
- Avoid extraneous whitespace.
- Avoid trailling whitespace.
```
Yes: spam(ham[1], {eggs: 2})
No:  spam( ham[ 1 ], { eggs: 2 } )

Yes: foo = (0,)
No:  bar = (0, )

yes:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

no:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```

### Assignment
- Use = for assignment.

### Indentation
- Use four spaces for indentation.
- Tabs should be used solely to remain consistent with code that is already indented with tabs.
- Otherwise, only use spaces.
- Continuation lines should align wrapped elements;
- Either vertically, using Python's implicit line joining,
- Or using a hanging indent.
- When using a hanging indent the following should be considered;
- There should be no arguments on the first line,
- Further indentation should be used to clearly distinguish itself as a continuation line.
```
# Add 4 spaces (an extra level of indentation) to distinguish arguments from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```

## SQL

SQL's code policy section was compiled by taking liberally from [Simon Holywell's style guide](https://www.sqlstyle.guide/). Please visit the link for more guidelines and to further clarify the guidelines below.

### General
- Use consistent and descriptive identifiers and names.
- Make judicious use of white space and indentation to make code easier to read.
- Store ISO-8601 compliant time and date information (YYYY-MM-DD HH:MM:SS.SSSSS).
- Try to use only standard SQL functions instead of vendor specific functions for reasons of portability.
- Keep code succinct and devoid of redundant SQL, such as unnecessary quoting or parentheses or WHERE clauses that can otherwise be derived.
- Include comments in SQL code where necessary.
- Use the C style opening /* and closing */ where possible otherwise precede comments with -- and finish them with a new line.

```
/* Updating the file record after writing to the file */
UPDATE file_system
   SET file_modified_date = '1980-02-22 13:19:01.00000',
       file_size = 209732
 WHERE file_name = '.vimrc';
 ```

- Avoid CamelCase. It's difficult to scan quickly.
- Avoid descriptive prefixes or Hungarian notation such as sp_ or tbl.
- Avoid plurals. Use the more natural collective term where possible instead.
- Avoid quoted identifiers. if you must use them then stick to SQL92 double quotes for portability (you may need to configure your SQL server to support this depending on the vendor).
- Avoid object-oriented design principles should not be applied to SQL or database structures.

### General naming conventions
- Ensure the name is unique and does not exist as a reserved keyword.
- Keep the length to a maximum of 30 bytes—in practice, this is 30 characters unless you are using multi-byte character set.
- Names must begin with a letter and may not end with an underscore.
- Only use letters, numbers and underscores in names.
- Avoid the use of multiple consecutive underscores—these can be hard to read.
- Use underscores where you would naturally include a space in the name (first name becomes first_name).
- Avoid abbreviations and if you have to use them make sure they are commonly understood.

### Table naming conventions
- Use a collective name or, less ideally, a plural form.
- For example (in order of preference) staff and employees.
Do not prefix with tbl or any other such descriptive prefix or Hungarian notation.
Never give a table the same name as one of its columns and vice versa.
Avoid, where possible, concatenating two table names together to create the name of a relationship table. Rather than cars_mechanics prefer services.

### Spaces
- Spaces should be used to line up the code so that the root keywords all end on the same character boundary.
- Right align commands, left align actual column names and implementation specific details.
- This forms a river down the middle making it easy for the reader's eye to scan over the code and separate the keywords from the implementation detail.
- Rivers are bad in typography, but helpful here.
- Use spaces:
- Before and after equal signs (=),
- After commas (,),
- Surrounding apostrophes (') where not within parentheses or with a trailing comma or semicolon.
```
(SELECT f.species_name,
        AVG(f.height) AS average_height, AVG(f.diameter) AS average_diameter
   FROM flora AS f
  WHERE f.species_name = 'Banksia'
     OR f.species_name = 'Sheoak'
     OR f.species_name = 'Wattle'
  GROUP BY f.species_name, f.observation_date)
  ```

### Line spacing
- Always include newlines/vertical space:
- Before AND or OR,
- After semicolons to separate queries for easier reading,
- After each keyword definition,
- After a comma when separating multiple columns into logical groups,
- To separate code into related sections - helps to ease the readability of large chunks of code.
- Keep all the keywords aligned to the righthand side and the values left aligned.
```
SELECT a.title,
       a.release_date, a.recording_date, a.production_date -- grouped dates together
  FROM albums AS a
 WHERE a.title = 'Charcoal Lane'
    OR a.title = 'The New Danger';
```

### Indentation
- Joins should be indented to the other side of the river and grouped with a new line where necessary.
```
SELECT r.last_name
  FROM riders AS r
       INNER JOIN bikes AS b
       ON r.bike_vin_num = b.vin_num
          AND b.engine_tally > 2

       INNER JOIN crew AS c
       ON r.crew_chief_last_name = c.last_name
          AND c.chief = 'Y';
```

- Subqueries should also be aligned to the right side of the river and then laid out using the same style as any other query.
```
SELECT r.last_name,
       (SELECT MAX(YEAR(championship_date))
          FROM champions AS c
         WHERE c.last_name = r.last_name
           AND c.confirmed = 'Y') AS last_championship_year
  FROM riders AS r
 WHERE r.last_name IN
       (SELECT c.last_name
          FROM champions AS c
         WHERE YEAR(championship_date) > '2008'
           AND c.confirmed = 'Y');
```

