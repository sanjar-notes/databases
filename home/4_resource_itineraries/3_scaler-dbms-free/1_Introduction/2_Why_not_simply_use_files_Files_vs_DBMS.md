# 2. Why not simply use files Files vs DBMS
Created Tue Mar 19, 2024 at 8:38 AM

In programming languages we have fopen, fprintf, fscanf etc, why aren't these enough to store data?

In other words, why isn't the file system enough for data storage?

- Well, even the DBMS software uses files, at the end of the day.
- Also a DBMS can do everything a filesystem can, but the filesystem doing everything a DBMS can would require lot of extra effort.

But a DBMS takes care of many of the details of data, that would have been a lot of effort and non-reliable if a file system was used. Like:
1. Querying - has a specific language (instead of us having to code) to query information, and has constructs like indexing to make querying more efficient. 
2. Redundancy - DBMS avoids redundancy using tables and foreign keys. It also minimizes disk space.
3. Consistency - again, because data is interlinked using foreign keys, changing a piece of unique data still keeps the system consistent. Example: a customer detail is updated, and does not need a change on any of the 'purchases' made by that customer.
4. Data independence - DBMS hides low level details from the users (i.e. engineers, business people etc). SQL is declarative, and you can ask anything you want it, and it takes cares of the detail.
5. Security and Access control - parts of the database or certain tables can be access hidden since they may contain sensitive data that is not relevant to the work that a person is doing at the company. Example: a business dev needs to access transactions of customers, but has no need to access customer's personal information. DBMS allows us to have security and access control very easily. Had this been a file system data system, one would have to setup OS level access to files, and also separate data into files.
6. Abstraction and ease of data access - SQL is declarative. If you know SQL and what tables are available, that's enough. It avoids the need to know data structures, algorithms, operating systems, file systems etc at time of access.

After OS, DBMS is the most widely used piece of software in companies.