# SQL Overview
## Data Definition Language (DDL)
- Create, drop, or alter the relation schema

## Data Manipulation Language (DML)
- The *retrieval* of information stored in the database
	- a *query* is a statement requesting the retrieval of information
	- the portion of a DML that involves information retrieval is called a *query language*
- The *insertion* of new information into the database
- The *deletion* of information from the database
- The *modification* of information stored in the database

## Data Control Language
- Commands that control a database, including administering privileges and users

# Data Manipulation Language
## Comments
- One line comment: from `--` till end of line
- Multi line comment: from /* to \*\/ 
## SELECT
- Used for queries on single or multiple tables 
- Clauses of the SELECT statement
	- **SELECT:** lists the columns (and expressions) that should be returned from the query
	- **FROM:** indicate the table(s) from which data will be obtained
	- **WHERE:** indicate the conditions to include a tuple in the result
	- **GROUP BY:** indicate the categorisation of tuples
	- **HAVING:** indicate the conditions to include a category
	- **ORDER BY:** sorts the result according to specified criteria
- A result of an SQL `SELECT` command is a single relation
### Examples
#### One table query
- List the names of all Australian students
```
SELECT name
FROM Student
WHERE country='AUS'
```
- SQL doesn't allow '-' in identifiers (e.g. table or column names)
- SQL identifiers and keywords are case sensitive
#### Order-by
- List all students (name) from Australia in alphabetical order
```
SELECT name
FROM Student
WHERE country='AUS'
ORDER BY name
```
- 2 options (per attribute)
	- **ASC (default):** ascending order
	- **DESC:** descending order
- You can order by more than one attribute
	- e.g. `ORDER BY country DESC, name ASC`
### Duplicates
- To eliminate duplicates when calculating a query result, use the keyword `DISTINCT` after `SELECT`
	- e.g. list the countries where students come from
```
SELECT DISTINCT country
FROM Student
```
- The keyword `ALL` specifies that duplicates should not be removed (default)
```
SELECT ALL country
FROM Student
```
### Alternatives to Column Name
- An asterisk in the `SELECT` clause denotes "all attributes"
```
SELECT *
FROM Student
```
- The `SELECT` clause can use arithmetic expressions involving operations +,-,\*,/ and operating on constants/numeric-valued attributes
```
SELECT uos_code, title, credit_points*2, lecturer
FROM UnitOfStudy
```

### Renaming
- Rename relations and attributes using `AS`
```
old_name AS new_name
```
- Helps give result columns of expressions a meaningful name
- e.g. find the student ID, grade, and lecturer of all assessments for PHYS1001 and rename the column name empid as lecturer
```
SELECT sid, empid AS lecturer, grade
FROM Assessment
WHERE uos_code='PHYS1001'
```

## WHERE
- Specifies the condition that rows must satisfy, to be part of the result
	- similar to Boolean logic in maths, and Boolean conditions in programming
- Comparison operations in SQL (between values, either constant, or coming from columns of the database): =, >, >=, <, <=, !=, <>
- Comparison results can be combined using **and**, **or**, and **not**
- Comparisons can be applied to results of arithmetic expressions
- e.g. find all UoS codes for units taught by employee 1011 that are worth more than 4 credit points
```
SELECT uos_code
FROM UnitOfStudy
WHERE lecturer = 1011 AND credit_points > 4
```
### BETWEEN
- Called "range queries"
	- The range-ends are included in the range
	- The range ends must be from a data type with an order
- e.g. find all students (by SID) who gained marks in the credit range in a task of COMP5138
```
SELECT sid
FROM Assessment
WHERE uos_code = 'COMP5138' AND mark BETWEEN 65 AND 74
```

## String Operations
- String-matching operator for comparisons on character strings
	- `LIKE` is used for string matching
- Patterns are described using 2 special characters
	- %: matches any substring
	- \_: matches any character
- e.g. list the titles of all "COMP" units
```
SELECT title
FROM UnitOfStudy
WHERE uos_code LIKE 'COMP%'
```
- SQL also has:
	- ||: concatenation
	- converting from upper to lower case (vice versa)
	- finding string length, extracting substrings, etc

## String Constants
- SQL uses single quotes

## Regular Expression Matches
- Implemented as set of SQL functions
	- e.g. `REGEXP_LIKE(...)`
- What are regular expressions?
	- pattern consisting of character literals and/or metacharacters
	- metacharacters specify how to process a regular expression
		- () grouping
		- | alternative
		- \[] character list
		- . matches any character
		- * repeat preceding pattern 0, 1 or more times
		- + repeat preceding pattern 1 or more times
		- ^ start of a line
		- $ end of a line
e.g.
```
SELECT title
FROM UnitOfStudy
WHERE REGEXP_LIKE(uos_code, '^COMP[:digit:"]{4}')
```

## Date and Time in SQL

| SQL Type  | Example               | Accuracy | Description                        |
| --------- | --------------------- | -------- | ---------------------------------- |
| DATE      | '2012-03-26'          | 1 day    | a date (some systems include time) |
| TIME      | '16:12:05'            | 1 ms     | a time, often down to nanoseconds  |
| TIMESTAMP | '2012-03-26 16:12:05' |          |                                    |
| INTERVAL  |                       |          |                                    |

