# 1. INSERT
Created Sat Apr 13, 2024 at 12:49 PM

## DQL
The query constructs we saw earlier, like `SELECT` are categorized as DQL - data query language. A DBMS usually has many more features (including fundamental ones) like:
- DDL (Data Definition Language) - creating tables, setting constraints etc.
- DML(Data Manipulation Language) - adding/updating/deleting data
	- DQL (Data Query Language) - we have explored this.
- DCL (Data Control Language)
- TCL (Transaction Control Language)

### DML major features (keywords)
There are 3 major DML keywords - `INSERT`, `UPDATE`, `DELETE`.


## `INSERT`
Insert one or multiple rows. Need to specify atleast "required" values.

Syntax
```sql
INSERT INTO
table_name (colA, colB...)
VALUES (val1, val2, val3), (val4, val5, val6);

-- maid, INSERT INTO VALUES
```
```sql
INSERT INTO 
movies(id, name, year, rankscore)
VALUES
(412321, 'Thor', 2011, 7);
```
Multiple rows can be also added, comma separated
```sql
INSERT INTO 
movies(id, name, year, rankscore)
VALUES
(412321, 'Thor', 2011, 7),
(412322, 'Iron Man', 2008, 7.9),
(412323, 'Iron Man 2', 2010, 7);
```
Can insert into select columns also (assuming other columns accept NULL or have AUTO-INCREMENT set up):
```sql
INSERT INTO 
movies(name, year)
VALUES
('The Maze Runner', 2014),
('Maze Runner: The Scorch Trials', 2015),
('Maze Runner: The Death Cure', 2010);
```

Note:
- Column names can be omitted, i.e. just table name is enough if you're adding complete rows values (i.e. all columns).