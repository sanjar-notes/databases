# 4. Order By
Created Tue Apr 9, 2024 at 11:22 PM

Task: show movies list in recent-first order
### `ORDER BY`
This is used to specify sort order of the rows that will be returned.
Default order is ASC.

Syntax:
```sql
SELECT * FROM table_name ORDER BY columnA;
SELECT * FROM table_name ORDER BY columnA DESC;
```

```sql
SELECT name, rankscore, year FROM movies ORDER BY year DESC LIMIT 10;
```

- `ORDER BY` is not stable (sorting characteristic). i.e. rows with the same value (of i.e. ORDER BY column) may have different order in the result table as compared to original table. This is due to query-optimizer and internal data-structures/indices, and therefore there's no stability guarantees.
- `ORDER BY` is a keyword but has a space in it.

## Conclusion
`ORDER BY` is used to specify order of rows in the output.