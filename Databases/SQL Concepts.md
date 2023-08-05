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
- Used for queries on single or multiple tables 
- Clauses of the SELECT statement
	- **SELECT:** lists the columns (and expressions) that should be returned from the query
	- **FROM:** indicate the table(s) from which data will be obtained
	- **WHERE:** indicate the conditions to include a tuple in the result
	- **GROUP BY:** indicate the categorisation of tuples
	- **HAVING:** indicate the conditions to include a category
	- **ORDER BY:** sorts the result according to specified criteria
- A result of an SQL `SELECT` command is a single relation

## SELECT
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
