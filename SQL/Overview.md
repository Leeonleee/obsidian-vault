# Table of Contents
- [#SQL](Terminology)


# Terminology
## Data
Facts that can be recorded
- Important for users
- Persistent (unchanging)
## Database
A collection of data
- Usually large
- Usually contains all data needed to operate an organisation
## Database Management System (DBMS)
Software package designed to store and manage databases
- Allows shared access from many programs
# Importance of Data
- Day to day operation of an organisation relies on accurate data
- Long term planning in an organisation relies on accurate data
- Data is a major asset for an organisation
# Importance of a Database
- It is an asset
	- Historical data can guide enterprise strategy
	- It's of interest to other enterprises
- State of the database mirrors the state of the enterprise
# How to Store and Use Data
- Write many application programs which all use a shared collection of data, and that data is stored in a DBMS
- In large organisations, the DBMS is usually commercial
	- Oracle, MS SQLServer, IBM DB2, etc
- Smaller organisations or non critical parts of large organisations often use open source systems
	- PostgreSQL, MySQL, etc
	- Also really huge data such as Facebook's data on likes etc
- Users run application programs which access the data through the DBMS
	- Programs get the DBMS to retrieve data and return it to the application
	- Programs also can get the DBMS to update data based on user input
# Managing the Data
- Typically, data management is divided to achieve the goals:
	- High-level goals ("policy") set by organisational leaders
	- Settings, processes, etc ("mechanisms") determined by technical people
## Data Management Concerns
- Deciding what data to hold and remove
- Ensuring accuracy of the data
- Ensuring proper use of the data
- Ensuring efficient use of the data
## Data Management Decisions
- Performance users get, and the security of the whole system affects the way data is stored and the system configuration settings
	- What helps one may be bad for others
# Structure of Data
- In DBMSs, the database stores <mark>descriptions of the format of the data</mark>
	- This is called the "<mark>System Catalogue</mark>" or "<mark>Data Dictionary </mark>"
- e.g. you can find that each employee has:
	- Identifier: Integer
	- Name: String up to 30 char
	- Address: String up to 60 char
	- Salary: Integer
- This info is called metadata

# Relational DBMSs
- All data is seen by users as tables of related, uniformly structured information
	- No duplicate rows, order not important
	- Each entry is simple: integer, string, etc
	- Matching values in different tables indicate connections

| SuppID | SName  | Phone      |
| ------ | ------ | ---------- |
| 8703   | Heinz  | 0293513287 |
| 8731   | Edgell | 0378301293 |
| 8927   | Kraft  | 0299412020 |
|        |        |            |

| ProdID | Description            | SuppID |
| ------ | ---------------------- | ------ |
| 29012  | Peas with Mint, 400g   | 8731   |
| 30086  | Peas and Carrots, 450g | 8703   |
| 31773  | Salted Peanuts, 500g   | 8731   |

## Instance
- The contents of the database at a single time
	- Every update changes the instance
## Schema
- Describes the structure of data in a particular database
	- What tables exist
	- What the columns are called, the type of each
- The instance at anytime must fit the scheme
	- Scheme rarely changes
- e.g. Supplier(SuppID: int, SName: string, Phone: string)
- Can also include *integrity constraints* to restrict the possible instances
	- e.g. each supplier has a different SuppID
## Data Design
- The process of deciding on the scheme that will be sued for the data
- Stages:
	1. produce a conceptual/semantic model
	2. translate into a relational schema
	3. evaluate the schema for quality and improve if needed
## Languages
### DDL (Data Definition Language)
- Used to define the schema
- Tells the DBMS what tables exist, and their structure
### DML (Data Manipulation Language)
- Used to access the data
- Includes commands to update the contents of the database and to retrieve information from the database

- For a relational database, both DML and DDL are in SQL
	- SQL is declarative in style (programmer describes what is needed, not how to find it)
	- SQL is a standard, but each vendor has variations
	- Applications are written to call the DBMS through SQL commands
## SQL Example
### Select-From-Where
- Retrieves data (rows) from one or more tables of a relational database that fulfil a search condition
e.g.1 "What is SuppID and Phone of the supplier named Heinz?"
```
SELECT SuppID, Phone
FROM Supplier
WHERE SName='Heinz'
```
e.g.2 "How many products come from supplier whose SuppID is 8703?"
```
SELECT Count(*)
FROM Product
WHERE SuppID=8703
```
- Can also connect data from several tables
e.g. "Show the ProdID of any product which is supplied by Heinz"
```
SELECT ProdID
FROM Supplier, Product
WHERE Product.SuppID = Supplier.SuppID and Supplier.SName='Heinz'
```
## Declarative Query
Considering the above query, which shows the ProdID of any product which is supplied by Heinz
- There are many ways for the system to calculate the output for this
	- Look through Product table row by row
		- For each product take the SuppID, then find it in the Supplier table and check if SName is correct. If it is, output
	- Look through Supplier table row by row
		- Check SName, if it is correct, take the SuppID then go through Product table checking each row to see if the SuppID is there
	- There are more possibilities
- Given a user provided query, DBMS should find a computation that is correct and fast, then give the user the answer
## Levels of Abstraction
Many views, single logical schema and physical schema
- View: how a user sees the data
- Logical schema: structure of data as it is shared among users
- Physical schema: files and indexes used for storage on disk
## Data Independence
- Applications are insulated from how data is structured and stored
- Logical data independence: Protection from changes in logical schema
	- e.g. from introducing an extra column in a table
- Physical data independence: Protection from changes in physical structure and location of data
- One of the important benefits of using a DBMS

# Career and People
- End users
- DB application programmers
- Database administration (DBA)
- DBMS vendor staff
## End Users
People who do something that advances the organisation's purpose
- Often unaware they are dealing with data in a DBMS
	- They simply run applications that present data to them and make controlled changes
- Categories:
	- Off-line naive users who get reports
		- e.g. manager gets weekly profit report
	- Parametric naive users who execute pre-written applications
		- e.g. manager runs application to reorder item
	- Ad hoc users who explore data
		- e.g. manager looking for trends
## Application Programmers
Produces the applications that end users can run
- Need to understand how to create an application that access data through a DBMS
## Database Administration (DBA)
Responsible for effective and efficient use of resources in providing access to data
- Example tasks:
	- Design logical/physical schema
	- Handle security and authorisation
	- Data availability, crash recovery
	- Database tuning
## DBMS Vendor Staff
Each vendor (Oracle, IBM, Microsoft etc) employ staff to help sell more installations, helping organisations that have bought the software
- DBMS implementors
- Tools development
- Training staff
- Sales support staff
- Operational support staff
-
# Big Ideas
## Metadata as Data
- The schema and other metadata is essential to working with data
	- Data is useless if one can't interpret it
	- Over time, the people who know what a value/string is may leave the organisation
- Metadata should be stored with the data it describes
## "What" not "How"
- Convenient to indicate *what* info is needed, and let the system work out *how* to process the data and retrieve what you need
- Users should be offered a way to express requests declaratively
	- Query language can be based on logic
	- Select...Where...
## Administrative Services
- A system should offer administrators an interface to adjust parameters, choose structure, set permissions, etc
# DBMS vs Others
- You an have a database without a DBMS to store it