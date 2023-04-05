# 5. Database Engine info
18 April 2022
- [ ] in vault

#### Why do we need database engines?
Database engine is just a fancy name for software that manages storage and access of data in a database.


#### Components of a database engine
They can be broadly divided into 3:
1. Storage manager - manages storing of database data in parts.
	- Important because databases typically require a large amount of storage space - even upto Petabytes (i.e. 1024 Terabytes).
	- Since the main memory of a machine is negligible compared to database size, data is stored on disk. Data is moved between main memory and disk as needed.
	- Since the movement of data between main memory and disc is slow, transfers need to be minimized.
2. Query processor - helps the database system to simplify and facilitate access to data.
	- It allows users to work at the view level with good performance while not being burdened by the low level details.
	- Its job is to translate queries and updates written in non-procedural language, at the physical level, into efficient sequence of operations at the physical level.


- While database engines where traditionally centralized computer systems, today parallel processing is key for handling very large amounts of data efficiently.
- Modern database engines pay a lot of attention to parallel data storage and parallel query processing.


#### Component 1 - Storage manager
- The raw data are stored on the disk using the file system provided by the OS.
- The storage manager is responsible for interaction with the file system. This includes the translation of DML statements into low-level file-system commands. Thus, the storage manager is responsible for storing, retrieving and updating data in the database.
- Components of the storage manager:
	1. **Authorization and integrity manager** - which tests for the satisfaction of integrity constraints and checks the authority of users to access data.
	2. **Transaction manager** - ensures that the DB remains in a consistent (correct) state despite system failures, and that concurrent transactions proceed without conflicts.
	3. **File manager** - manages allocation of space on disk storage and the data structures used to represent information stored on disk.
	4. **Buffer manager** - responsible for fetching data from disk into main memory, and deciding what/how-much to cache in main memory. The buffer manager is a critical part of the database system, since it enables the database to handle data sizes that are much larger than the size of the main memory.
- The storage manager implements several data structures as part of the physical system implementation:
	1. Data files - which store the database itself.
	2. Data dictionary - stores metadata about the structure of the database, in particular the schema of the database.
	3. Indices - these are data structures that intended for quick access of a table. Like the index of a textbook, a database index provides pointers to those data items that hold a particular value. For example - we could use an index to find the *instructor* record with a particular *ID*, or all *instructor* records with a particular *name*.

Storage media, file structures and buffer management are discussed ahead.


##### Component 1.2 - Transaction manager
- An operation is some change in the database that doesn't guarantee consistency.
- A transaction, OTH, is a sequence of operations, that are guaranteed to be atomic and consistent.
- Why have a *transaction* constuct?
	- Allows application developers to treat a sequence of database accesses as if they were a single atomic access.
	- This permits thinking at a higher level of abstraction about the application without needing to be concerned with the lower-level details of managing the effects of concurrent access to data and of system failures.

Example - transfer some money from Account A to Account B. This can be thought of as a transaction, made up of two operations:
- Deduct the amount from A. This makes the database inconsistent, temporarily
- Add the amount to B. The database is now consistent.

The transaction is a meticulous construct, since it involves a safety and failure-prevention part, at each of the operations - which is handled by the **recovery manager**.

This was a simple case. But a more practical scenario is when concurrent transaction take place, which are consistent individually, but can make the database inconsistent. The **concurrency-control manager** ensures consistency in this case.

Both of these sub-components - the **recovery manager** along with the **concurrency-control manager** make up the **transaction manager**.


#### Component 2 - Query processor
Components include:
- DDL interpreter - interprets DDL statements and records the definitions in the data dictionary.
- DML compiler - translates DML statements in a query language into evaluation plan consisting of low-level instructions that the query-evaluation engine understands. A query can usually be translated into any of a number of alternative evaluation plans that give the same result. The DML compiler performs **query optimization**, i.e. it picks the lowest cost evaluation plan from among the alternatives.
- Query evaluation engine - executes low-level instructions generated by the DML compiler.

Query evaluation, and query optimization are discussed ahead.