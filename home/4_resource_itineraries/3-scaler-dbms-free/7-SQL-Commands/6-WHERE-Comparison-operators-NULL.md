# 6. WHERE Comparison operators NULL
Created Wed Apr 10, 2024 at 12:15 AM

Task: List all movies with a rank-score of 9 or higher.

## `WHERE`
Syntax:
```sql
SELECT * FROM table_name WHERE condition_expression;
```

Examples:
```sql
SELECT DISTINCT name, year, rankscore FROM movies WHERE rankscore > 9;

--

SELECT name, year, rankscore FROM movies WHERE rankscore>9 ORDER BY rankscore DESC LIMIT 20;
```

Note:
- Since our condition was `rankscore > 9`, movies with `NULL` rating are absent since the condition is not satisfied.
- The order of where `WHERE` appears in the query is important. It should appear just after the `FROM`, otherwise we get a syntax error. (WHY!)

## `WHERE` conditions
- Condition outputs can be TRUE, FALSE or NULL, and these are usable [literals](https://dev.mysql.com/doc/refman/8.0/en/boolean-literals.html) too.
- Allowed operators: =, <, >, <=, >=, != (aka <>)
- Strings and other non-numbers can use =, != (aka <>) just fine.
- =, != (aka <>) don't work with NULL value, i.e. `=NULL`, `!=NULL` won't work. Have to use `IS NULL` and `IS NOT NULL` to do the comparison successfully.

More operators and constructs also exist like propositional and predicate expressions. Will learn about them next.

## Conclusion
`WHERE` is meant for doing selection (as defined in Relational algebra), i.e. filter out rows w.r.t some boolean condition.

i.e. it helps filter or search rows.