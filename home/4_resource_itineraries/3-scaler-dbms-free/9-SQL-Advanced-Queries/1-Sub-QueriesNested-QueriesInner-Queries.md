# 1. Sub QueriesNested QueriesInner Queries
Created Thu Apr 11, 2024 at 5:14 PM

## Task
In our IMDB dataset, we have 3 tables:
```sql
mysql> DESCRIBE actors;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| id         | int          | NO   | PRI | 0       |       |
| first_name | varchar(100) | YES  | MUL | NULL    |       |
| last_name  | varchar(100) | YES  | MUL | NULL    |       |
| gender     | char(1)      | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> DESCRIBE roles;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| actor_id | int          | NO   | PRI | NULL    |       |
| movie_id | int          | NO   | PRI | NULL    |       |
| role     | varchar(100) | NO   | PRI | NULL    |       |
+----------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> DESCRIBE movies;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| id        | int          | NO   | PRI | 0       |       |
| name      | varchar(100) | YES  | MUL | NULL    |       |
| year      | int          | YES  |     | NULL    |       |
| rankscore | float        | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```

We want to make pages like so - i.e. given movie id:
![](../../../../assets/1-Sub-QueriesNested-QueriesInner-Queries-image-1-20089a66.png)

## Solution - subqueries
How would we do it?
1. One way is to do a 3 way JOIN and apply movie id filter
2. Other way is to divide the work
	1. Find given movie's id
	2. Find out all actors in that movie
	3. Find name of actors
	4. Combine 1, 2, 3 to get all info (see screenshot above)
	   But this is not possible with out current knowledge, since we can't have isolated result-sets that are again used in the same query.
	   
	   But SQL does allow it. It does so via implicit variables (i.e. implicit queries).

```sql
SELECT first_name, last_name FROM actors WHERE id IN 
	(SELECT actor_id FROM roles WHERE movie_id IN 
		(SELECT id FROM movies WHERE name='Schindler\'s List')
	);
```


- Sub-queries are also called nested queries.
- The idea of subqueries in the direct sense means nesting and temporary variable storage, but in SQL they can only be used with the `WHERE` clause. Important to know this constraint in the language.

## Correlated subquery
Correlated subquery - A subquery that uses a variable from its outer query. It's like a looping happy case where outer scope's variable is used.

```sql
SELECT employee_number, name
FROM employees emp
WHERE salary > (
	SELECT AVG(salary)
	FROM employees
	WHERE department = emp.department);
```

Note:
- Correlated subqueries are helpful, but may be expensive.
## `IN`, `ANY`, `ALL`
*Both are misnomers in the programming sense, since they are not general conditional functions. they're just for comparison.*

- `ANY` - return TRUE if the comparison is TRUE for ANY of the values in the column that the subquery returns. Identical to `SOME`
- `ALL` - return TRUE if the comparison is TRUE for ALL of the values in the column that the subquery returns
- `IN` - return TRUE if the ~~comparison~~ (equality) is TRUE for ANY of the values in the column that the subquery returns. Difference between `IN` and `=ANY`, `IN` accepts both lists and result-set, but `=ANY` accepts only result sets.

Both are O(n<sup>2</sup>) ops in general

```sql
SELECT *
FROM orders
WHERE (product_id, quantity) > ALL 
(
    SELECT product_id, quantity
    FROM products
    WHERE category = 'Electronics'
);

-- SELECT ∗ FROM orders WHERE (product_id,quantity) is greater than ALL rows of subquery
```

```sql
SELECT *
FROM orders
WHERE (product_id, quantity) > ANY 
(
    SELECT product_id, quantity
    FROM products
    WHERE category = 'Electronics'
);
-- SELECT ∗ FROM orders WHERE (product_id,quantity) is greater than any rows of subquery
```

## `EXISTS`
Checks if subquery is non-empty or not. Like a `.length` operator.
If a subquery returns any rows at all, EXISTS subquery is TRUE, and NOT EXISTS subquery is FALSE.

- `NOT EXISTS` is the opposite.
- Unrelated to ANY, ALL or IN.

```sql
SELECT *
FROM categories c
WHERE EXISTS 
(
    SELECT 1
    FROM products p
    WHERE p.category_id = c.category_id
);
```