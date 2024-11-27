# 8. Aggregate Functions COUNT MIN MAX AVG SUM
Created Wed Apr 10, 2024 at 1:21 AM

## Task
What is the highest rankscore ever assigned to any movie.

## Context
All SQL statements we learnt until now (SELECT, WHERE etc) returned a table.
But sometimes we want to calculate a single (scalar) value, like getting total, count, avg, min, max etc.

In SQL, these operations are done using 'Aggregate functions'. Essentially they are an array.reduce operation (think JS `Array.reduce`)

The count 50,000 below is calculated using an aggregate function
![](../../../../assets/8-Aggregate-Functions-COUNT-MIN-MAX-AVG-SUM-image-1-90a59cee.png)
## Syntax
```sql
SELECT aggregate_function(columnA) FROM table_name;

-- specifically, the syntax is
SELECT aggregate_function(columnA)

-- note: there should be no space between function and opening parentheses
COUNT (year) ❌ -- syntax error
COUNT(year)  ✅
```

Examples:
```sql
SELECT MIN(year) FROM movies;
SELECT MAX(year) FROM movies;
SELECT COUNT(*) FROM movies;
SELECT COUNT(*) FROM movies WHERE year > 2000; -- conditional counting is possible!
SELECT COUNT(year) FROM movies;
-- COUNT(year) gives the same result as COUNT(*) since
-- COUNT doesn't care about column values, but just the existence of rows
```

Outputs
```sql
mysql> SELECT MIN(year) FROM movies;
+-----------+
| MIN(year) |
+-----------+
|      1888 |
+-----------+
1 row in set (0.15 sec)


mysql> SELECT MAX(year) FROM movies;
+-----------+
| MAX(year) |
+-----------+
|      2008 |
+-----------+
1 row in set (0.09 sec)


mysql> SELECT COUNT(*) FROM movies;
+----------+
| COUNT(*) |
+----------+
|   388269 |
+----------+
1 row in set (0.03 sec)


mysql> SELECT COUNT(*) FROM movies WHERE year > 2000;
+----------+
| COUNT(*) |
+----------+
|    46006 |
+----------+
1 row in set (0.08 sec)


mysql> SELECT COUNT(year) FROM movies;
-- COUNT(year) gives the same result as COUNT(*) since
-- COUNT doesn't care about column values, but just the existence of rows
+-------------+
| COUNT(year) |
+-------------+
|      388269 |
+-------------+
1 row in set (0.09 sec)
```

Note: 
- aggregate functions ignore NULL values

## Aggregate functions
There are 5 aggregate functions:
1. COUNT
2. SUM
3. AVG
4. MAX
5. MIN
## Output of aggregate queries is also a table
Even though the value is a scalar, we still get output as a table.
It's a single-column-single-row table with column name being the aggregate part of the query, and value is the computed value.

```sql
mysql> SELECT COUNT(year) FROM movies;
+-------------+
| COUNT(year) |
+-------------+
|      388269 |
+-------------+
```


## Important cases
### Duplicates
In all the functions, duplicates are considered. To not count duplicates again, use `SELECT COUNT(DISTINCT Price)`. i.e. mark the column as distinct.

### Empty source set - returning NULL
Except `COUNT`, all other functions return `null` if run against an empty table (or result set). `COUNT` will result in 0.

### Aggregate functions support callbacks
- COUNT (expression) - include or not
	- COUNT(column) - will ignore NULLs. TRUE AND FALSE, 1 and 0 everything is treated as true.
- SUM (expression) - returnage value is added.
- AVG (expression) - returnage value is added, but COUNT(\*) is still done. Even nulls are counted.
- Ternary `IF(condition, val1, val2)`.
```sql
SELECT COUNT(table.action = 'confirmed') 
	-- will couunt table.action = "confirmed", all others are not counted
FROM table;


-- another example with SUM
-- the value taken by SUM is returnage of the callback
SELECT SUM(table.action = 'confirmed') 
	-- will add 1
FROM table;
```
 - To include NULLs, add `OR IS NULL` condition, and for a default value in `SUM`, use COALESCE. `SUM(COALESCE(quantity, 1))`, if quantity is NULL, takes default value of 1.


## Conclusion
Aggregate functions are used in finding a reduced value (avg, sum, count) or min/max values.

Note: in case of MIN, MAX, the result is the optimal value, not the row having the optimal value, this is important.