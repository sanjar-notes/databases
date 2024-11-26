# 11. Order of keywords
Created Thu Apr 11, 2024 at 12:48 AM

https://sqlbolt.com/lesson/select_queries_order_of_execution
## Writing order of keywords
SQL keywords in a query need to be in a certain "proper" order. Otherwise you'll get an error.

The simple structure is `SELECT FROM WHERE extras`. 

But `SELECT` itself has a lot of sub-keywords. So it's not always easy to remember the order. This manual helps https://dev.mysql.com/doc/refman/8.0/en/select.html

Note:
- This is the order of SQL keyword in the query (i.e. code). I'm not talking about execution order, that is different.
- General query writing order is
	- Projection in RA
	- Source(s)
	- Selection in RA
	- extras like ORDER BY, LIMIT, OFFSET

## SQL execution order
A SQL query executes its statements in the following order:

1. FROM / JOIN - *makes sense, determine source(s), including making source by combining individual sources*
2. WHERE *makes sense, general filter removes unnecessary rows at the beginning itself*
3. GROUP BY - *makes sense, group (reduce) should happen after filter*
4. HAVING - *makes sense, this is a filter that works with group by only, but it's still a filter, so should happen early (but after group by)*
5. SELECT - *makes sense, decide column (i.e. discard info), only after all filter, aggregates are done*
6. DISTINCT *makes sense, deduplicate near the end since rows are all known at this point*
7. ORDER BY *makes sense, near the end, also avoid expensive sort on potential duplicates (if DISTINCT is present)*
8. LIMIT / OFFSET  *makes sense, truncate should be at the very end, doesn't mess up sort order, logics*

[source](https://x.com/NikkiSiapno/status/1758144066553004445)