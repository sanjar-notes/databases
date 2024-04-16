# 3. DROP TABLE TRUNCATE DELETE
Created Mon Apr 15, 2024 at 1:39 AM

- `DROP TABLE table_name;` - deletes both the table data and the schema
	- `DROP TABLE table_name IF EXISTS` - is a safe way to do table deletion. i.e. avoid the "table does not exist error".
- `TRUNCATE TABLE table_name;` - deletes all rows of the table, i.e. empty table still remains
- `DELETE FROM table_name` - same as TRUNCATE - i.e. deletes all row (default WHERE is true).