# 3. Database languages
18 April 2022
- [ ] in vault

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
- Query processor is the component of a database that translates declarative DML into a sequence of actions at the physical level of the database.
- Processing queries at the parallel and distributed settings is somewhat different when compared to a monolithic database. (TODO: really?)

#### About SQL
- SQL (Structured Query Language) is a declarative database language.
- Almost all relational database systems use SQL, or a variant of it.
- It was invented at IBM in 1974.
- It was the first language to use the relational model, based on Edgar F. Codds influential paper on the subject. Despite not completely adhering to the relational model as described in the paper, it is the most widely used database language.

#### Database access from Application programs
- Modern SQL is Turing complete.
- SQL does not support actions such as input from users, output to displays, or communication over the network, by default.
- Due to the above points (minor IO features), SQL queries are embedded in a general purpose programming language like C++, Java, Python etc. This language is also known as the *host* language.
- To access the database, DML statements need to be sent from the host to the database where they will be executed. This done via an API that's used to send queries and retrieve results. ODBC, JDBC are examples of API for the C, and Java language, respectively.