# 3. Database languages
#### Why database languages
- Manipulation (including access) to a database needs a uniform language. The goal is to allow humans to interact efficiently with the system.
- A query is a statement requesting retrieval of information.

#### Components of a database language
- There are basically 2 components, DDL and DML. But they are bifurcated further.
- The specific components of a database language:
	1. DDL (Data-definition language) - used to specify database schema, which includes consistency constraints.
	2. DQL (Data-query language) - used to express database queries.
	3. DML (Data-manipulation language) - expresses database updates. There are two kinds of DML - procedural and declarative.
	4. DCL (Data-control language) - used for setting up rights and permissions of parts of a database.
	5. TCL (Transaction-control language) - used to carry out database transactions.

#### Query processor and declarative DML
- Query processor is the component of a database that translated declarative DML into a sequence of actions at the physical level of the database.
- Processing queries at the parallel and distributed settings is somewhat different when compared to a monolithic database. (TODO: really?)

#### About SQL
- SQL (Structured Query Language) is a non-procedural database language.
- Almost all relational database systems use SQL, or a variant of it.
- It was invented at IBM in 1974.
- It was the first language to use the relation model, based on Edgar F. Codds influential paper on the subject. Despite not completely adhering to the relational model as described in the paper, it is the most widely used database language.