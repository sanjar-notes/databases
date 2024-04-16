# 2. ALTER ADD MODIFY DROP
Created Mon Apr 15, 2024 at 1:31 AM

Given a table, how do we change its schema (i.e. columns and constraints, not data)?

### 3 types of `ALTER`
There are 3 kinds of [ALTER](https://dev.mysql.com/doc/refman/8.3/en/alter-table.html) operations:
1. `ADD` - add a column
   ```sql
   ALTER TABLE table_name ADD column_name type extras...; -- add column
	```
2. `MODIFY` - change a column. i.e. ~~name~~ (?), type and constraints. `ALTER TABLE table_name DROP column_name`
   ```sql
   ALTER TABLE table_name MODIFY column_name type extras...; -- modify column
	```
3. `DROP` - delete a column. `ALTER TABLE table_name DROP column_name`
   ```sql
   ALTER TABLE table_name DROP column_name; -- delete column
	```