# misc
Created Thu Nov 14, 2024 at 1:00 AM

## Aliases
https://www.w3schools.com/sql/sql_alias.asp
### Types
- Aliases - there are table and column aliases. Table aliases are used for re-reference in nested queries. Column aliases change column label in the result set.

### Uses of aliases
- Nested queries
- Combining columns - columns of the result set can be combined i.e. 2 columns can be combined by concatenation (say) to produce a single column. You'd need an alias for the new combined column of course.
	- This can be used to create new columns also. The new columns temporarily and redundant of course. Like repeating a column name will add the same column again the result set. Useful for presentation.
	- This is super useful since SQL does not differentiate between numbers and will coerce numerical strings to numbers and do the calculation. Will be zero for NaN.
```sql
	SELECT CustomerName, 
	Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
	FROM Customers;

	-- yes this really combines the data
```

## UNION
Combine two result sets rows. Both result sets must have the same columns.
 Syntax is simple.
```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

- `UNION ALL` is a variant will do also de-duplicate rows.
- Columns in UNION/ALL remain the same.

## Helper operators
- LENGTH
- SUBSTRING
- `DATE_FORMAT(T.trans_date, '%Y-%m')`


## Index-seekable vs table-scan queries
Sometimes a problem can be solved using two different equivalent (return same result) queries, but one of the queries can utilize indexes if they are present, and the other cannot.

It's better to prefer the one that can utilize indexes. These queries are called "index-seekable".

Of course, without the index both are the same.

Example:
```sql
-- index-seekable
-- O(n) if index on employee_id
-- better
SELECT Employee.employee_id, Employee.department_id 
FROM Employee 
WHERE 
    Employee.primary_flag = 'Y' 
        OR 
    Employee.employee_id IN 
        (
            SELECT DISTINCT EmployeeClone.employee_id 
            FROM Employee AS EmployeeClone 
            GROUP BY EmployeeClone.employee_id 
            HAVING COUNT(*) = 1
        );
```

vs

```sql
-- table-scan (can never utilize an index)
-- perf: m * n in any case
-- not good
SELECT DISTINCT Employee.employee_id, Employee.department_id
FROM Employee
WHERE 
	Employee.primary_flag = 'Y' 
	OR 
	(SELECT COUNT(*) FROM Employee AS EmployeeClone WHERE EmployeeClone.employee_id = Employee.employee_id) = 1;
```