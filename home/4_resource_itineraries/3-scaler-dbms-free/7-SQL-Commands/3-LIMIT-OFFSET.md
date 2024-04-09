# 3. LIMIT OFFSET
Created Tue Apr 9, 2024 at 11:09 PM

## Task: Implement pagination
Suppose the movies list page shows only 20 movies at a time, and there are 'Next' and 'Previous' button to show the next or previous 20 movies. How will the SQL look for this feature?

## `LIMIT`
Used to limit, i.e. specify max number of rows to be returned.
```sql
SELECT name, rankscore FROM movies LIMIT 20;
```

will return 20 rows.
If table size < 20, it will return all that is present.

note: the output will contain the *first* 20 rows here.


## `OFFSET`
Used to ignore first `n` rows, and return the rest.
```sql
SELECT name, rankscore FROM movies OFFSET 20;
```

If the table had movies with id 1 to 50, this will skip the first 20, i.e. only rows with id 31 to 50 will be returned.

## `LIMIT` and `OFFSET` together
Since both keywords don't collide (obviously), they can be used together.
```sql
SELECT name, rankscore FROM movies LIMIT 20 OFFSET 40;

-- same as (skipping and limiting, or limiting and skipping are equivalent)
SELECT name, rankscore FROM movies OFFSET 40 LIMIT 20;
```

The keywords don't collide because limit is considered at the end of the query execution cycle, since it's purely about max return count. So both queries the queries when compiled, will have the same internal code, and therefore, same result.

Since this is SQL we don't need to concern ourself with low level details of how to get the result. We just specify 'what' we want and we're done.

## Conclusion
- LIMIT is used for specifying max output rows
- OFFSET is used to set initial skip count