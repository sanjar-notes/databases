# misc
Created Thu Nov 14, 2024 at 1:00 AM

## Types
- Aliases - there are table and column aliases. Table aliases are used for re-reference in nested queries. Column aliases change column label in the result set.

## Uses of aliases
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
