# Leetcode
Created Fri Nov 22, 2024 at 1:09 AM

- COALESCE is like nullish coalescing. COALESCE (val, 0) would evaluate to val if is not NULL, otherwise 0 (or whatever default specified).
	- Its better to use COALESCE at intermediary expression if default values are needed. Graceful fallback. If default values are not required, and the whole calc is ignored, then once at SHELL is fine.
	- NULL + NULL, or any arithmetic op is NULL.
- CASE statements
	- Used within aggregate functions
	- Used for better displaying
  ```sql
	CASE
	    WHEN condition1 THEN result1
	    WHEN condition2 THEN result2
	    ...
	    ELSE default_result
	END
	
	-- example
	SELECT 
    column,
    CASE 
        WHEN column > 10 THEN 'High'
        WHEN column > 5 THEN 'Medium'
        ELSE 'Low'
    END AS level
	FROM table;
	```
- ROUND 2