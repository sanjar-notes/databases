# 1. Tuple Relational Calculus I
Created Fri Apr 5, 2024 at 1:32 AM

### Comparison with other languages
We have discussed about 3 querying languages:
1. Relational algebra - Operators selection, projection, rename, set-difference, cartesian-product, natural-joins. It's a procedural.
2. Tuple relational calculus (TRC). It's declarative.
3. SQL - It's declarative

## Edgar Codd and math foundation of SQL
Edgar Codd was a mathematician and computer-scientist who made all these languages, and also many theoretical constructs in relational databases at IBM research in the 1970s-80s. He came up with mathematical foundations for his work, giving us reliable constructs to work with data.

TRC is the mathematical foundation of SQL

## TRC's logics
TRC is heavily based on propositional and predicate logic.

See the different kind of logics:
![](../../../../assets/1-Tuple-Relational-Calculus-I-image-1-bb0f4323.png)

## A Query in TRC
A query in TRC looks like a set of.

The condition parts contains operators from first-order-logic, viz AND, OR, NOT, there-exists, for-all, element-of.
![](../../../../assets/1-Tuple-Relational-Calculus-I-image-2-bb0f4323.png)

continue from https://www.scaler.com/topics/course/dbms/video/474/ (6:46)