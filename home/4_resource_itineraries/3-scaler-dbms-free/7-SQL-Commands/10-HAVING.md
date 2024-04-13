# 10. HAVING
Created Wed Apr 10, 2024 at 11:34 PM

Task: What are the years where more than 1000 movies were released

## Solution
Essentially, we want to group, aggregate count, then filter rows (stay if count > 1000).
So this *can* be done using `GROUP BY` with a `WHERE` clause. OK, since one query can have only one `WHERE` clause, just use a subquery. *Checked, I get a syntax error since you can't use an alias declared in a nested subquery outside it (SQL is like C, no closures)*.

But, SQL has the `HAVING` sub-feature/syntax-sugar to make our life easier.
It works only when used with `GROUP BY`.

## What happens inside `HAVING`
Fundamentally, these steps happen, i.e. `GROUP BY` + 1 filter step:
1. grouping - `GROUP BY` internal step 1
2. aggregate - `GROUP BY` internal step 2
3. filter - extra step 


## Syntax
Since 3 steps, we need 3 inputs:
1. Grouping column
2. Aggregate function, w.r.t a column.
3. Filter condition. Since aggregation is done already, we can filter only w.r.t the aggregate values. *So an using a alias in the HAVING expression is a must.*

```sql
SELECT year, COUNT (year) movie_count FROM movies GROUP BY year HAVING movie_count > 1000;

-- actually COUNT(any_column) would have worked, since it's COUNT (column or value doesn't matter)
```

## `WHERE` vs `HAVING`
tl;dr, use `HAVING` only with `GROUP BY`, [KISS](https://en.wikipedia.org/wiki/KISS_principle).

If you don't heed the above, the rules are still simple:
- If `GROUP BY` is absent, `HAVING` is exactly the same as `WHERE`.
- Scope: If both are present, then `WHERE` is applied on the source table rows, and `HAVING` (of course `GROUP BY` is also present) is applied on `GROUP BY` internal aggregate values.
- Order - if both are present, WHERE is executed first, and HAVING is executed later (and only on internal values of GROUP BY, above point).
- You can't use code `GROUP BY WHERE`, i.e. only `GROUP BY HAVING` is allowed. Strange but ok, maybe SQL wants to delineate general filter vs group filter.
- You can't have two `HAVING` in the same query.

## Conclusion
 Use `GROUP BY columnA HAVING expression` when want to filter out groups aggregate values.