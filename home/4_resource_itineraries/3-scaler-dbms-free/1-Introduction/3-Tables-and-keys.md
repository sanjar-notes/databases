# 3. Tables and keys
Created Tue Mar 19, 2024 at 9:10 AM

The "relation" word in "Relational databases" is related to "sets and relations" in math. There's a whole algebra called "Relational algebra" that deals with relations.

There are many kinds of databases, including non-relational ones, like graph databases.

## Table
- A table has columns and rows.
- A table is also called a *relation*.
- A column is also called a *attribute/field*.
- A row is also called a *tuple/record*.

An actual instance (i.e. contains data) of a table = set of tuple/rows + a table structure


## Why table
Instead of thinking about data, programs or automation, lets think of how data is obtained.
So, without tech/computers, we tell stories (i.e. represent situations) about something. And in a given story, there may be multiple instances of the same kind of thing (object). Also, these objects interact with each other. This effectively gives us the constructs of tables:
1. Multiple instances of the same type of thing - represents linear repetition, i.e. table. Each instance becomes a row.
2. Each object has certain inherent properties, these become attributes of that object's table.
3. Since objects interact - with other types of object, or even with the same kind. That leads to links between tables.

Lets consider an alternative (to the above) story where we'd not need table, and try to think about a construct to represent it. So this story has objects, but only one instance of an object is present. The objects may relate to one another. This leads to the logical structure of a graph where nodes are objects and edges are relations, but, this graph is static, it never changes. So there's nothing to record or update here, i.e. it's not a data system (although it does capture non-zero information), i.e. there's nothing to manage/maintain here. *In short, this is a potentially boring story, and the real world does have a lot of multiplicity, and parts of it we're interested in are mostly not like this boring story, hence we need tables*.

Knowing that tables help tell stories helps realize that DBMS and SQL may seem mechanical, but the end goal is to work with stories, so it's not a dry work or goal.

## Key and types of keys
A key is a *minimal set* of attributes to uniquely identify a row.

Example: In the customers table, customerId is a key. But \[customerId, customerName] is not a key, because it is not "minimum" even if it's still unique. Something like \[CustomerName, CustomerAddress] is most likely a key, since people with the same names usually don't live at the same place.

A key has to be unique among rows, but can be NULL (multiple NULLs are also fine).

Some terms:
- Simple key - a key with only one attribute. Example: customerId
- Compound key - a key with multiple attributes. Example: \[CustomerName, CustomerAddress]
- Primary key - a key that the DB-designer/DBA/dev *chooses* (i.e. choice aka arbitrary) to maintain uniqueness among rows of a table.
	- Very often a simple key is chosen as the primary key. 
	- It is ensured that PK is not null and unique, reasonably so since it is like an identifier.
	- There should be at-most one PK.
- Candidate keys set - the set of *all unique* keys that are *possible* for the table. Every candidate key is minimal, i.e. a subset of the candidate key won't be a key (i.e. not useful in uniquely determining a row). There can be multiple candidate keys for a given table.
- Entity integrity constraint - the fact that the above three conditions are satisfied.

A subtle detail - PK cannot be null, but other candidate keys may have a null value. So this is the primary diff between PK and candidate keys.

- Alternative/secondary keys - candidate keys that are not PKs.
- Relational schema - info about structure about all tables and integrity constraints that tables have to satisfy.
- Super key - a compound key formed by combining a candidate key and any other attribute(s). A set. mAID superset. Super key cannot be a null set. There can be multiple super keys for a given table.
- Foreign key - an attribute in the current table that is a primary key in some other table. The other table may be the current table too (self referential).
	- Concept wise, it acts as a pointer to a row in the other table. Example: customer and purchases table, where purchases table has customerId as a attribute.
	- All foreign key values have to exist in the other table, this is checked during row creation in current table. 
	- Advantages of having foreign key:
		- Avoids redundancy
		- Avoids edit inconsistencies, i.e. the row in other table can be changed without worrying about the current table (had we copied the attribute from the other table).
	- Self referential foreign keys. Example: a employees table with employeeId, employeeName and managerId. Here managerId is a FK to the employeeId attribute, of the same table, with the CEO having null as managerId.
	- Foreign keys may be null.