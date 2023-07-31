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
- Can also include 