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

### Connecting Multiple Tables
- Limit the results to pairs which match up properly
	- Put a matching condition (join-predicate) in the where clause
	- If the same column name appears in multiple tables used, you need to qualify it in a `WHERE` conditions or in a `SELECT` lists by preceding with the relation name, then fullstop
		- e.g. `Student.sid` is the sid value from the Student table
- e.g. Find the student ID, name, and gender of all students enrolled in ISYS2120
```
SELECT Student.sid, name, gender
FROM Student, Enrolled
WHERE Student.sid = Enrolled.sid AND uos_code = 'ISYS2120'
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
| TIMESTAMP | '2012-03-26 16:12:05' | 1 sec    | time at a certain date             |
| INTERVAL  | '5 DAY'               | years-ms | a time duration                    | 

### Comparisons
- normal time-order comparisons with =,>,<,<=,>=,...
### Constants
- `CURRENT_DATE`: database system's current date
- `CURRENT_TIME`: database system's current timestamp
### Example
```
SELECT name
FROM Student
WHERE enroldate < CURRENT_DATE
```
### Operations
- Unfortunately they're not very standardised
- Main operations
	- `EXTRACT(component FROM date)`
		- e.g. `EXTRACT(year FROM enroldate)`
	- `DATE string` (Oracle syntax: `TO_DATE(string,template)`)
		- e.g. `DATE '2012-03-01'`
		- Some systems allow templates on how to interpret string
		- Oracle syntax: `TO_DATE('01-03-2012', 'DD-Mon-YYYY')`
	- `+/- INTERVAL`
		- e.g. `'2012-04-01' + INTERVAL '36 HOUR'`
- Check database system's manual for more operations

## FROM
- Lists the relations involved in the query
	- If there's more than 1 table, it is the Cartesian product (all pairs, one from each table) of discrete maths
	- Find the Cartesian product Student x UnitOfStudy
		```
		SELECT *
		FROM Student, UnitOfStudy
		```
	- This is very rarely what the user wants
### Aliases
- Aliases can be given to the relation name in the `FROM` clause
- Ailias follows the relation name
```
SELECT S.sid, S.name, S.gender
FROM Student S, Enrolled
WHERE S.sid = Enrolled.sid AND uos_codee = 'ISYS2120'
```
- Why?
	- Some queries need to refer to the same relation twice
	- Makes reading/typing easier
- e.g. with same table used twice: For each academic, retrieve the academic's name, and the name of his or her's immediate supervisor
```
SELECT A.name, M.name
FROM Academic A, Academic M
WHERE A.manager = M.empid
```

## Joins
- **Join:** one of the relational operations that cause 2 or more tables to be combined into a single table of view
- **Equi-join:** joining condition is based on equality between values in the common-named columns; matched columns appear redundantly in the results table
- **Natural join:** like equi-join, but only one of the duplicate-named columns is kept in the result table
- **Outer join:** rows that don't have matching values in common columns are included in the result table
- **Inner join:** rows must have matching values to appear in the result table
- **Union join:** includes all columns from each table in the join, and an instance for each row of each table
### Join Operators
- `R NATURAL JOIN S`
	- put together rows, one from each table, in which the same-named columsn have the same values
- `R INNER JOIN S ON <join condition>`
- `R INNER JOIN S USING (<list of attributes>)`
- the keyword `INNER` can be left out, as its the default
- `ON` or `USING` are needed with `INNER JOIN`
- These are often used as expressions in the `FROM` clause
### Examples
1. List all students and in which courses they enrolled
```
SELECT name, uos_code, semester
FROM Student NATURAL JOIN Enrolled
```
2. Who is teaching "ISYS2120"?
```
SELECT name
FROM UnitOfStudy JOIN Academic on lecturer=empid
WHERE uos_code='ISYS2120'
```

## Aggregate functions
- Operate on the multi-set of values of a column of a relation, and return a value
	- `AVG`: average value
	- `MIN`: minimum value
	- `MAX`: maximum value
	- `SUM`: sum of values
	- `COUNT`: number of values
- These combine data from many rows into a single row
- Each one operates on a single column of values
	- Except `COUNT(*)` which counts how many rows meet the `WHERE` condition
### Aggregates and Duplicates
- Often use `DISTINCT` to ensure the aggregate is over a set
	- eliminates duplicates among the values being aggregated
	- no difference between multi-set and set for `MAX`, `MIN`
- e.g. How many Australian students are enrolled (in any class)?
	- We don't want to count the same student repeatedly
```
SELECT COUNT(DISTINCT)
```