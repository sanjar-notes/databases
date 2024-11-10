# 5. Distinct
Created Wed Apr 10, 2024 at 12:00 AM

Task: list all the movie genres in the database. Of course, genres may repeat so omit duplicates in the result list.

## `SELECT DISTINCT`
By default, even if the output of a query has duplicate rows, SQL will still keep them (unlike relational algebra).

This is useful if you really want all instances to be kept, i.e. SQL ensures data is not lost.

But, sometimes, you don't want duplicates. To do this, use the `SELECT DISTINCT` keyword instead of just `SELECT`, and it'll remove duplicate rows from the final output.

```sql
SELECT DISTINCT genre FROM movies_genres;
```

Note:
- practical usage - suppose all rows in the UI listing (in the example app we're building) have certain values (enum) for a certain column, and we wish to add a filter for that attribute. Then `SELECT DISTINCT` can be used to generate the entries of this filter (assume filter is a dropdown).

## `SELECT DISTINCT` with multiple columns
`SELECT DISTINCT` allows dedup w.r.t multiple columns. But be careful, the dedup that happens here is w.r.t the "concatenated" (actually series of equalities) value of the columns, i.e. rows can have duplicates for one column. But the whole set of columns specified will never repeat.

See explanation below (this output is valid, even though first_name is repeated if seen in isolation)
![](../../../../assets/5-Distinct-image-1-90a59cee.png)

- Note: `SELECT DISTINC *` would dedup rows.
## Conclusion
`SELECT DISTINCT` is used to deduplicate rows of a table, w.r.t one or more columns.