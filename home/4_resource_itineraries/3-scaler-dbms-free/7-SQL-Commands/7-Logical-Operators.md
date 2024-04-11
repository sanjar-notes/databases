# 7. Logical Operators
Created Wed Apr 10, 2024 at 12:40 AM

Task: List movies released after 2000 with rankscore higher than 9.

As we can see there are two conditions here, the only way to make the query is to do a boolean AND.
This is easily possible and allowed by the `WHERE` clause, since it also supports propositional and predicate expressions. So the query will be:
```sql
SELECT name, year, rankscore FROM movies WHERE rankscore>9 AND year>2000;
```

## Logical and operators
Usual boolean operators, used with statements, no change here.
- AND - binary operator
- OR - binary operator
- NOT - unary operator
## More operators
### `BETWEEN` (range membership)
check if value is in given range
```sql
SELECT * FROM table_name WHERE columnA BETWEEN lowValue AND highValue;
--

-- specifically, condition syntax is
BETWEEN lowValue AND highValue;
```

```sql
SELECT name, year, rankscore FROM movies WHERE year BETWEEN 1999 AND 2000;
-- #inclusive: year>=1999 and year<=2000
```

Note:
- if lowValue is higher than highValue, you'll get empty result. This happens because this doesn't make any sense. There will be no warning/error here either, so be careful.
- This is a short-form for two comparison statements: `columnA >= lowValue AND columnA <= highValue`

### `IN` (set membership)
Check if value is in a set (i.e. list). The list can be comma-separated or even a result set (but it should have only one column).
```sql
SELECT * FROM table_name WHERE columnA IN ('value1', 'value2', 'value3');

SELECT * FROM table_name WHERE columnA IN (resultSetWithOneColumn);

-- specifically, condition syntax is
columnA IN ('value1', 'value2', 'value3');
```

```sql
SELECT director_id, genre FROM directors_genres WHERE genre IN ('Comedy', 'Horror');
-- same as genre='Comedy' OR genre='Horror"
```

- Works only for discrete sets, not ranges.
- This a short-form for writing n statements separated by OR, where each statements is an equality check.

### `LIKE` (pattern matching)
Used for regular expression matching, but the expression language is a little different.
```sql
SELECT * FROM table_name WHERE columnA LIKE 'some_pattern';
-- % = wildcard character to imply zero or more characters

-- specifically, condition syntax is
columnA LIKE 'some_pattern'
```

```sql
SELECT name, year, rankscore FROM movigs WHERE name LIKE 'Tis%';
-- return rows where name starts with 'Tis'

SELECT first_name, last_name FROM actors WHERE first_name LIKE '%es';
-- return rows where first_name ends with 'es'
```

More wildcard characters:
- `%` means 0 or more characters
- `_` (underscore) means exactly one character

note:
- To match '%' or '\_' itself (i.e. literally), use backslash as escape character, i.e. `\%`, `\_`
- Of course NOT LIKE is possible, but it's just a logical negation of LIKE. Example:
  ```sql
	SELECT first_name, last_name
	FROM actors 
	WHERE first_name LIKE 'L%' AND first_name NOT LIKE 'Li%';

	-- this is a valid query
	```
### others

- EXISTS
- 
- SOME
- EXISTS - quantifier, used in subqueries, will discuss ahead
- ALL - quantifier, used in subqueries, will discuss ahead
- ANY - used in subqueries, will discuss ahead