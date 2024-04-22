# 3. Solved problems 1
Created Sun Apr 21, 2024 at 8:53 PM

Video: https://www.scaler.com/topics/course/dbms/video/506/

1. Simple. Process query in proper execution order (FROM, WHERE, GROUP BY, SELECT), then find out that group by controls number of entries, ignore the rest of the query.
2. Basic - full outer join is the largest, and also contains all results from inner-join (aka natural join), left-inner-join, right-inner-join. So it's a superset.
3. Simple - evaluate the subquery. Since it has group by, that'll control number of rows in result-set. Then see the outer query, it's just a aggregate function. Calculate. Answer is single value.
4. Consider the subqueries first, the first one is always true, and the second one is also simple. Essentially it's a MAX condition. Filter out rows in original table that satisfy, done.
5. 'WITH' is syntax sugar that helps save results of subqueries in a variable. Mentally execute top down (note that latter WITHs can access WITH variables declared before them, makes sense). Finally execute the main (last) query. *WITH is syntax sugar to make some kind of subqueries simple to represent*.