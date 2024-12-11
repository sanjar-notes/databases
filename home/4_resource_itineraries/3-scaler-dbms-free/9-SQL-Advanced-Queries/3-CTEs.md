# 3. CTEs
Created Thu Dec 12, 2024 at 12:29 AM

## What and why
CTEs are a reuse construct in SQL.
Internally a temporary table is created, that is persisted as long as queries use it. Then its deallocated.

## Syntax
```sql
-- one CTE
WITH MyTempTable AS (builder_query_here)
actual_query;
```

```sql
-- can create multiple CTEs
WITH MyTempTable1 AS (builder_query_here3),
WITH MyTempTable2 AS (builder_query_here3),
WITH MyTempTable3 AS (builder_query_here3)

actual_query;
```

```sql
-- alias for CTE columns is supported
-- no need of AS in col aliases at CTE declaration
WITH MyTempTable (col1_alias, col2_alias) AS (builder_query_here)
actual_query;
```
## CTEs can be used for one query only
Its not possible to have CTEs (one or more) with more than one query.
This is because separating actual query requires a semicolon, and that will mark de-allocation for CTEs.

```sql
WITH MyTempTable AS (
    SELECT * FROM SomeTable
)
SELECT * FROM MyTempTable; -- Works

SELECT * FROM MyTempTable; -- Fails: MyTempTable no longer exists
```

The alternatives, if u want to do this are:
1. Make a temporary table explicitly and use it.
2. Combine the queries into one, by using UNION etc.