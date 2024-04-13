# 9. GROUP BY
Created Wed Apr 10, 2024 at 9:57 PM

Task: List down number of movies released each year

## Misnomer alert
 `GROUP BY` in SQL doesn't do just grouping. 
 It does both grouping and aggregation, i.e. it has an extra reduce step that is mandatory.
 
Let me clarify why it's a misnomer. Consider JS:
```js
const inventory = [
  { name: "asparagus", type: "vegetables", quantity: 5 },
  { name: "bananas", type: "fruit", quantity: 0 },
  { name: "goat", type: "meat", quantity: 23 },
  { name: "cherries", type: "fruit", quantity: 5 },
  { name: "fish", type: "meat", quantity: 22 },
];

const groups = Object.groupBy(inventory, (food) => food.type);

/* Result is:
{
  vegetables: [
    { name: 'asparagus', type: 'vegetables', quantity: 5 },
  ],
  fruit: [
    { name: "bananas", type: "fruit", quantity: 0 },
    { name: "cherries", type: "fruit", quantity: 5 }
  ],
  meat: [
    { name: "goat", type: "meat", quantity: 23 },
    { name: "fish", type: "meat", quantity: 22 }
  ]
}
*/
```
The JS's groupBy function is intuitive. It took some rows and grouped them w.r.t a criteria.

But SQL `GROUP BY` does this:
```js
let result = Object.groupBy(inventory, (food) => food.type); // JS stops here, but SQL is yet to finish
result = Object.entries(result).reduce((accum, ([key, items])) => ({[key]: items.reduce(aggregateLogic(items))}), {});

/*
if aggregate logic was COUNT, then the final result would be
{
  vegetables: 1,
  fruit: 2,
  meat: 3
}
*/
```
i.e. SQL `GROUP BY` does not return the rows in the groups, but an aggregate of such rows (per group).

## Syntax
Since SQL `GROUP BY` is a two-step operations - group and reduce. It needs two inputs - a column to group by and an aggregate function to perform the reduce operation.

```sql
SELECT AggregateFunction(columnB) FROM table_name GROUP_BY columnA;

-- the following is also possible since columnA is the group criteria, i.e. it's value is the same for a group's rows (i.e. in a way it is preserved)
SELECT columnA, AggregateFunction(columnB) FROM table_name GROUP_BY columnA;

-- specifically,
AggregateFunction(columnB) FROM table_name GROUP BY columnName;
```

You can't have free columns (i.e. columns other than aggregate or grouping column) - reason is obvious, the rows are not present in groups, only the aggregate is.
Also, since groups are mutually exclusive, there can only be one aggregate column. So there can be atmost 2 columns in a `GROUP BY` query.
```sql
SELECT columnC, AggregateFunction(columnB) FROM table_name GROUP_BY columnA; -- error, grouped on A, aggregate values for groups generates on B, now there's no way to include C (unsolvable because groups have many rows, which value of C would you print??)
```

Examples:
```sql
SELECT COUNT (name) FROM movies GROUP BY year; -- grouping and aggregation specified, OK.

SELECT year, COUNT (year) FROM movies GROUP BY year; -- since year is the group criteria, yes it can be included usually in output, since it's preserved

SELECT year, COUNT (year) FROM movies GROUP BY year ORDER BY year; -- order by is the last code to run, doesn't affect GROUP BY

SELECT year, AVG (rankscore) FROM movies GROUP BY year; -- grouping and aggregation are different, so can be done on different column, OK.
```


## `GROUP BY` multiple columns
tldr, grouping criteria by multiple columns. This is not something very different or fundamental.
We use "serial matching" (i.e. concatenated value or concatenated similarity hashes) of columns as the grouping criteria, instead of just one column.

Syntax:
```sql
SELECT columnA, columnB, AggregateFunction(columnC)
FROM table_name 
GROUP BY columnA, columnB;


-- general syntax will be
SELECT columnA, columnB ..., AggregateFunction(ColumnAA)
FROM table_name
GROUP BY columnA, columnB ...;
```

For clarity, lets consider the internal steps of `GROUP BY`:
1. Grouping - grouping is now done based on "{columnA} {columnB}"
2. Aggregate - aggregate is done on groups' rows, as usual (they are still rows from the source table)

## Conclusion
*Use SQL `GROUP BY` if you want to calculate values of groups (exclusive groups) in a table*.

You'll need to provide grouping column, as well as the aggregate function. Grouping is based on equality/similarity.

Also, SQL does not return group's rows and the groups are mutually exclusive, so SELECT columns have just one aggregate column.

Start https://www.scaler.com/topics/course/dbms/video/493/