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


## Key
A key is a *minimal set* of attributes to uniquely identify a row.

Example: In the customers table, customerId is a key. But \[customerId, customerName] is not a key, because it is not "minimum" even if it's still unique. Something like \[CustomerName, CustomerAddress] is most likely a key, since people with the same names usually don't live at the same place.

- Simple key - a key with only one attribute. Example: customerId
- Compound key - Key with multiple attributes. Example: \[CustomerName, CustomerAddress]
- Candidate key - set of all unique keys.
- Primary key
resume from video https://www.scaler.com/topics/course/dbms/video/461/ 13:40