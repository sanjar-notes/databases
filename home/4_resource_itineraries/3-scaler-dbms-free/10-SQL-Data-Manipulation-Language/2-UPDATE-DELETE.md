---
tags:
  - clone-table
---
# 2. UPDATE DELETE
Created Sat Apr 13, 2024 at 1:45 PM

## `UPDATE`
Update a row, i.e. one or more columns of the row
```sql
UPDATE table_name SET col1=val1, col2=val2...
WHERE condition_expression;

-- maid, UPDATE SET WHERE
```

## `DELETE`
Delete a row
```sql
DELETE FROM movies WHERE id=412321; -- be careful, omitting WHERE will delete all rows

-- maid, DELETE FROM WHERE
```

Note:
- Delete all rows - `TRUNCATE TABLE table_name`. Same as delete without a `WHERE` clause. This deletes all rows, but the table still exists (empty now).
## Cloning a table
There are two steps:
1. Create table with the schema, auto-increments etc i.e. all ticks.
2. Add data
```sql
CREATE TABLE new_table LIKE old_table; -- new table has the schema as well as other setup copied

INSERT INTO new_table (SELECT * FROM old_table); -- copy data
```

Note
- To clone a table without extra ticks like auto-increment, use this:
  ```sql
	CREATE TABLE new_table (SELECT * FROM original_table WHERE FALSE); -- clone table, empty, only column types copied

	CREATE TABLE new_table (SELECT * FROM original_table); -- same as above, but with data
	```
