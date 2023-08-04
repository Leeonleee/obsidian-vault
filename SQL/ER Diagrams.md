# Table of Contents
- [Graphical Notation for Relational Schema](<# Graphical Notation for Relational Schema>)

# Graphical Notation for Relational Schema
For each table: TableName, open bracket, columns names in order each with type separated by comma, closing bracket
```
Supplier(SuppID: int, SName: string, Phone: string);
Product(ProdID: int, Descr: string, SuppID: int);
```

- Sometimes you can leave out the data type information (implicit)
## Constraints
- Show a column that is unique among rows of a table by underlining the column name
	- Can serve as an identifier
	- Called the *primary key* of the table
- Other tables can include this identifier as a column to make connections to the given table
e.g. Product(<u>ProdID</u>: int, Descr: string, SuppID: int)
- ProdID is the identifier column for Product table
## Relational Schema Diagrams
- Can include types or leave them out
- Can list column information horizontally or vertically
- Underline primary key (identifier)
- Show an arrow from the referring column/table it the one where the values are found as identifier
## Composite Primary Key
- In some tables, no single column can serve as identifier because repeat values are possible
- A combination of columns may be suitable
	- Not allowed for 2 rows to match values in every one of the columns involved
- A combination of columns makes a composite primary key
	- Shown in schema/diagram by underlining all column names involved
e.g. SupplierCountryOffice(<u>SuppID</u>, <u>CountryCode</u>, StreetAddress, Postcode)

| SuppID | CountryCode | StreetAddress                   | Postcode |
| ------ | ----------- | ------------------------------- | -------- |
| 8703   | AUS         | 271 George Street, Sydney       | 2000     |
| 8703   | USA         | 56 Fifth Avenue, New York       | 10001    |
| 8731   | AUS         | 300 Elizabeth Street, Melbourne | 3000     |
| 8731   | NZL         | 21 Queen Street, Auckland       | 0600     |
| 8731   | USA         | 401 Broadway, New York          | 10001    |
| 9031   | KOR         | 40 Dongdaemun Plaza, Seoul      | 01000    |
- This ensures that no 2 rows have the same SuppID and the same CountryCode so (SuppID, CountryCode) can be a composite primary key
## Data Model
2 meanings
1. A model of the structure of a database
	- Schema for that database
2. The modelling approach that is used for the schema
	- relational model, document model, etc


# Conceptual Data Model
## Conceptual Design
- A technique for understanding and capturing business information requirements
***
- *Conceptual database design* does not tell how data is implemented, created, modified, used or deleted
	- Facilitates planning, operations & maintenance of various data resources
## Types of Conceptual Data Models
- Entity-Relationship Model (ERM)
- Object-oriented Data Models
	- Unified Modelling Language (UML)
- Other approaches
	- Object Role Modelling (ORM)
	- Semantic Object Model (SOM)
	- Semantic Data Models (SDM)
	- KL-ONE etc
# Entity Relationship Model
- Data model for conceptual database design
	- High-level graphical representation of what data needs to be contained in the system
- Data modelling approach that depicts the association among different categories of data within a business/information system
	- What are the *entities* and *relationships* in the enterprise?
	- What info about these entities and relationships should we store?
	- What integrity constraints/business rules are there?
- A database schema is represented by ER diagrams
- It is about what data needs to be stored
	- does *not* tell how data is implemented, created, modified, used or deleted

## Entities
- **Entity:** a person, place, object, event or concept about which you want to gather and store data
- **Entity Type (aka Entity Set):** a collection of entities that share common properties or characteristics
	- e.g. students, courses, accounts
	- represented by a *rectangle*
- **Attribute:** describes one aspect of an entity type
	- e.g. people have *names* and *addresses*
	- represented by an *ellipse* that is connected to the entity type rectangle
### Entity Type
- Described by a set of attributes
	- e.g. Person has ID, Name, Address, Hobbies
#### Domain
Possible values of an attribute
- Unlike relational model, values can be complex/set-oriented
- *Simple* and *composite* attributes
	- A composite attribute is where the value for an entity has distinct parts
	- e.g. Address has parts: housenumber, streetname, suburb
- *Single-valued* and *multi-valued* attributes
	- A multivalued attribute is where an entity might have more than one value associated to it
	- e.g. a person might have several hobbies
#### Primary Key
- The primary key (PK) for an entity type is an attribute/combination of attributes that uniquely identifies an entity
	- Every entity in the set has a different value for that attribute
	- Depicted by underlining that attribute
- There may be more than one attribute that distinguishes the entities
	- Any attribute that does this is called a **key**
- **Entity Schema:** entity type name, attributes (+domains), PK
## Entity Types and Attributes in ER Diagram
### Symbols
- **Entity Type:** rectangle
- **Attribute:** ellipse
	- **Multi-valued Attribute:** double ellipse
	- **Keys:** underlined
	- High-level description may leave out attributes or show them elsewhere
## Relationships
- Related or connects 2 or more entities (often from different entity types)
	- **Degree:** number of entities in the relationship
	- e.g. John *is enrolled in* ISYS2120
		- *"is enrolled in"* is a relationship between Student and Subject
		- degree is 2
- **Relationship Type (aka Relationship Set):** is a set of similar relationships (entities are from the same type)
	- e.g. Student (entity type) related to Subject (entity type) by EnrolledIn(relationship type)
		- EnrolledIn relationship type involves 2 entity types, so its a binary relationship type
### ER Diagram
- **Relationship Type:** diamond
	- Labelled with the name of the relationship
- Lines connect the involved entity types to the relationship type

### WARNINGS
- A relationship in an ER conceptual model is **NOT** a relation in the relational model (which is a set of tuples)
	- The info about a relationship and entity type may be captured in a relation in a relational schema
## Relationship Attributes & Roles
- **Relationship-Attribute:** relationships can have additional properties
	- e.g. John enrols in ISYS2120 as an elective
		- John and ISYS2120 are related
			- Elective is the value of the degree_role attribute for this relationship
		- Jane enrolles in ISYS2120 as a core unit
		- EnrolledIn relationship type has a degree_role attribute
- **Relationship-Role:** each participating entity can be named with an explicit role
	- e.g. John is a value of Student role, ISYS2120 is a value of Subject
		- You can use the name of the Entity type as the role name (optional, but common)
	- Explicit names for roles are useful for a relationship that related elements of the same entity type
		- e.g. Supervises is a relationship type between 2 employees, one with role Manager, and the other with Subordinate role
## Graphical Representation of Relationships in ER Diagrams
- **Relationship Type:** diamond
- **Attribute of Relationship Type:** ellipse
- **Connecting involved entity types to relationship type:** lines
- **Roles:** edges labelled with role names
	- Role label is often omitted when same as entity name
## Relationship Degree
- **Degree:** number of entity types involved
	- Unary relationship (recursive)
	- Binary relationship (most common type)
	- Ternary relationship (3 entity types involved)
## Multiplicity of a Relationship
- **Many-to-many Relationship:** the number of instances of the other entity set to which one instance is connected to is unrestricted
- **Many