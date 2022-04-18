# 2. View of data
18 April 2022
- [ ] in vault

- A **major purpose** of a database system is to provide users with an *abstract* view of the data. 
- Abstract view means that the users shouldn't have to worry about the low level data structures, algorithms and details of the programs of the database system, i.e. how the data is stored and maintained should be abstracted away.

#### What is a data model
- Underlying the structure of the database is the *data model*: a collection of conceptual tools for describing:
	- data
	- data relationships
	- data semantics
	- consistency constraints

#### Data models
Some data models are:
1. Relational model - data and relations among it are represented as a collection of tables. 
	- Each table has multiple columns, and each column has a unique name.
	- Tables are also known as "relations".
	- It is also known as a record-based model, because each record defines a fixed number of attributes (or fields).
	- It is the most widely used data model.
2. ER model - entity-relationship (ER) model uses a collection of basic objects, called *entities* and *relationships* among these objects. An entity is a "thing" or "object" in the real world that is distinguishable from other objects. TODO: rephrase this.
3. Semi-structured data model - this model permits the specification of data where individual data items of the same type may have different sets of attributes.
	- This is different from relational and ER model, where each data item has the same set of attributes.
	- JSON and XML are widely used semi-structured data representations.
4. Object-Based model - OOP is a dominant software-development methodology. This model actually saves individual objects as data items. This model can be seen as relational data model with notions of encapsulation, methods and object identity. TODO: how does it differ from ER model?

- Most of this book is focused on the relational model because it serves as the foundation for most database applications.

#### Data abstraction (levels)
There are 3 levels of data abstraction for a database system:
1. Physical level - describes *how* data is actually stored and maintained, i.e. describes the complex low level data structures and algorithms.
2. Logical level - describes the data and relationships among them. DBAs, programmers use this level of abstraction.
3. View level - the highest level of abstraction, describes a relevant part of the database. The same database system may have many views of the database for different stakeholders, based on their need. Here, only data is shown, without relationships to other data, TODO: really only data without relationships? Example - a college clerk.

- An important feature of data models is they hide low-level implementation even from the database-application developers.

#### Instances and Schemas
- Databases change over time as data is inserted, updated or deleted.
- Instance - the collection of information stored in the database at a particular moment.
- Schema - the overall design of the database. 
	- Databases have several schemas, partitioned according to the level of abstraction.
	- *Physical schema* describes the database design at the physical level, *logical schema* describes the database design at the logical level. 
	- A database may also have several schemas at the view level, sometimes called "subschemas", that describe different views of the database.
- Physical schema is hidden beneath the logical schema, and can usually be changed without affecting application programs.
- Traditionally, logical schemas were changed infrequently. But newer database applications require flexible logical schema, as records of the same type may have different attributes.
- Bad schemas are possible, and defining schemas is a crucial part of database (use) design.