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
- A result of an SQL SELECT command is a single relation

## Example
### One table query
- List the names of all Australian students
```
SELECT name FROM Student WHERE country='AUS'
```
- SQL doesn't allow '-' in identifiers (e.g. table or column names)
- SQL identifiers and keywords are case sensitive
### Order-by
- List all students (name) from Australia in alphabetical order

