# 1. CREATE TABLE
Created Sat Apr 13, 2024 at 1:52 PM

https://sqlbolt.com/lesson/creating_tables

`CREATE DATABASE`
```sql
CREATE DATABASE db_name;
CREATE DATABASE IF NOT EXISTS db_name; -- safe way to create a table
```

## `CREATE TABLE`
Create a table.
```sql
CREATE TABLE table_name 
(colName type extras...), 
(colName type extras...)
...; 
```

Note:
- `extras` refers to constraints and other fine grained setup.
- Order of extras matters. `id INT AUTO_INCREMENT PRIMARY KEY` will work, but `id INT PRIMARY KEY AUTO_INCREMENT` will not.
- `CREATE TABLE IF NOT EXISTS table_name...` is a safe way to create a table;
## Data types
Some types are just one word, while others take a param (like varchar).

Here's a list. Note that not all databases support all types.
![](../../../../assets/1-CREATE-TABLE-image-1-b3eb175e.png)

So, there are basic types like 
- precise numbers, float numbers
- date, time, timestamp (UNIX)
- fixed sized strings, max-size-fixed strings, dynamic size strings, unicode strings.
- types for storing binary data, images
- Special purpose data like JSON, XML, Blob


## FOREIGN keys
Syntax is simple.
You specify column and the type, but there's an additional phrase for the foreign key column
```sql
CREATE TABLE children 
(
	id INT,
	name VARCHAR(50),
	
	parent_id INT, -- foreign key name and type
	FOREIGN KEY (parent_id) REFERENCES parents(id) -- extra phrase needed
);
```
The reference to other column is like function notation, instead of dot notation.

## Constraints
These are constraints on values that are stored in a given column. The databases always validates these, after all operations, and throws and error if they're not satisfied.

- NOT NULL - cell value cannot be null. Otherwise throw error.
- UNIQUE - all values in the column are unique. NULL's are acceptable and ignored for uniqueness.
- PRIMARY KEY - NOT NULL and UNIQUE. meant to act as row identifier
- FOREIGN KEY - a link (i.e. primary key of row) to another table
- CHECK - user defined constraint. Throws error if not met. Example: value > 0
- DEFAULT - default value for a column if not specified
- INDEX - a construct defined for a given column that speeds up reads and joins. May hamper writes. Practically, a table almost always has an index on some column.