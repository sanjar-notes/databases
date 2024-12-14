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

F## `WHERE` conditions
- Condition outputs can be TRUE, FALSE or NULL, and these are usable [literals](https://dev.mysql.com/doc/refman/8.0/en/boolean-literals.html) too.
- Allowed operators: =, <, >, <=, >=, != (aka <>)
- Strings and other non-numbers can use =, != (aka <>) just fine.
- =, != (aka <>) don't work with NULL value, i.e. `=NULL`, `!=NULL` won't work. Have to use `IS NULL` and `IS NOT NULL` to do the comparison successfully. https://sqlbolt.com/lesson/select_queries_with_nulls

More operators and constructs also exist like propositional and predicate expressions. Will learn about them next.

## Incomparability of NULL
Get all users who don't have the teacher with id = 2;
```sql
SELECT * FROM Users WHERE teacher_id != 2; -- is not enough. is incorrect.

SELECT * FROM Users WHERE teacher_id !=2 OR teacher_id IS NULL; -- is correct
```

i.e. NULL cannot be compared with anything, even themselves. Actually even `teacher_id = NULL` is wrong.


## Conditionals with `NULL`
When SQL encounters a conditional expression involving NULL. It uses the following rules:
- `AND`: The result of `true` and `unknown` is `unknown`, `false` and `unknown` is `false`, while
`unknown` and `unknown` is `unknown`.
- `OR`: The result of `true` or `unknown` is `true`, `false` or `unknown` is `unknown`, while `unknown` or `unknown` is `unknown`.
- `NOT`: The result of not `unknown` is x`unknown`.

## Conclusion
`WHERE` is meant for doing selection (as defined in Relational algebra), i.e. filter out rows w.r.t some boolean condition.

i.e. it helps filter or search rows.