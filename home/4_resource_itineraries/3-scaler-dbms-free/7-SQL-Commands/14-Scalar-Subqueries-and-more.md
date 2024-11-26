# 14. Scalar Subqueries and more
Created Sat Nov 16, 2024 at 11:27 PM

SQL is quite flexible in treating result sets.

Here’s a quick rundown of key SQL rules where result sets can be treated as lists or scalars in different contexts:

### 1. **Scalar Subqueries (Single Value Result Set)**:
   - A subquery that returns **one value** (one row, one column) can be used **where a scalar value is expected** (like in `WHERE`, `HAVING`, or `SELECT`).
   - **Example** (instead of hardcoding value of Chicago `41.87`):  
     ```sql
     SELECT city
     FROM cities
     WHERE population > (SELECT population FROM cities WHERE city = 'Chicago');
     ```

### 2. **Single-Column Result Set (List)**:
   - A result set with **one column** and multiple rows is treated as a **list of values**.
   - Can be used with `IN`, `ANY`, or `ALL` operators.
   - **Example**:  
     ```sql
     SELECT city
     FROM cities
     WHERE country IN (SELECT country FROM cities WHERE population > 1000000);
     ```

### 3. **`IN` with Subquery (List of Values)**:
   - The result set from a **single-column subquery** is automatically treated as a **list** of values.
   - **Example**:  
     ```sql
     SELECT city
     FROM cities
     WHERE country IN (SELECT country FROM cities WHERE population > 1000000);
     ```

### 4. **`ANY` / `SOME` with Subquery (Single Value Comparison)**:
   - A subquery with **one column and multiple rows** can be used to compare a value against **any value** from the result set.
   - **Example**:  
     ```sql
     SELECT city
     FROM cities
     WHERE population > ANY (SELECT population FROM cities WHERE country = 'USA');
     ```

### 5. **`ALL` with Subquery (All Values Comparison)**:
   - A subquery with **one column and multiple rows** can be used to compare a value against **all values** from the result set.
   - **Example**:  
     ```sql
     SELECT city
     FROM cities
     WHERE population > ALL (SELECT population FROM cities WHERE country = 'USA');
     ```

### 6. **`EXISTS` with Subquery**:
   - `EXISTS` checks if a subquery returns **any result set** (can be 1 row, 1 column or multiple rows and columns). It doesn’t care about the values, only whether rows exist.
   - **Example**:  
     ```sql
     SELECT city
     FROM cities
     WHERE EXISTS (SELECT 1 FROM countries WHERE countries.name = cities.country);
     ```

### 7. **`UNION` and `UNION ALL` (Combining Result Sets)**:
   - **`UNION`** combines results from multiple queries into a single result set, removing duplicates. It treats multiple queries' results as a combined list of values.
   - **`UNION ALL`** combines results without removing duplicates.
   - **Example**:  
     ```sql
     SELECT city FROM cities WHERE population > 1000000
     UNION
     SELECT city FROM cities WHERE population <= 1000000;
     ```

### 8. **`JOIN` (Merging Multiple Result Sets)**:
   - **INNER JOIN**, **LEFT JOIN**, **RIGHT JOIN** combine multiple result sets (tables or subqueries), creating a **composite list**.
   - **Example**:  
     ```sql
     SELECT c.city, c.country, p.product
     FROM cities c
     JOIN products p ON c.country = p.country;
     ```

### 9. **Aggregates with `GROUP BY` (List of Aggregated Results)**:
   - Aggregated results (like `SUM`, `AVG`, `COUNT`) create a list of computed values, often used with **`GROUP BY`**.
   - **Example**:  
     ```sql
     SELECT country, COUNT(*) 
     FROM cities 
     GROUP BY country;
     ```

### 10. **`DISTINCT` (Unique List of Values)**:
   - **`DISTINCT`** removes duplicate rows, treating the remaining rows as a **unique list**.
   - **Example**:  
     ```sql
     SELECT DISTINCT country FROM cities;
     ```

### Key Points:
- **Scalar Subqueries** are treated like a single value.
- **Single-Column Subqueries** are treated as lists of values.
- Operators like `IN`, `ANY`, `ALL` and `EXISTS` can work with subqueries returning multiple rows.
- **`UNION`** and **`JOIN`** treat multiple result sets as combined lists.

