# 2-Cardinality-of-relationships-and-constructing-minimal-tables. 
Created Tue Mar 26, 2024 at 10:45 PM

## Cardinality of relations
There are 4 possible cardinalities of relationships:
1. one-one. Example: customer "has a" driver's license
2. one-many. Example: a mother "has" many children
3. many-one. Example: All children "have" a mother
4. many-many. Example: People "studied" in school

Note: non-participating elements are ignored.

TBH, this was covered in class 12th in sets and relations.

## Cardinality and participation
 Total or partial depends on participation, and definition of cardinality ignores non participating entity instances (elements). This makes the possibility space of \[total, partial] x \[1-1, 1-n, n-1, n-n] visible large.

We will explore nuances of these combinations later.


## Cardinality representation conventions
There are many. All are equivalent. Different people prefer different notation, no problem.

![](../../../../assets/2-Cardinality-of-relationships-and-constructing-minimal-tables-image-1-6718f520.png)

We'll use this:
- 1 side - arrowed line with 1 label
- many side - simple line with variable as label
- Double lines means total, single line means partial participation
![](../../../../assets/2-Cardinality-of-relationships-and-constructing-minimal-tables-image-2-6718f520.png)
## Constructing tables from ER diagrams*, using general algorithm and cardinality-participation value*
During transformation, we need to take care/consider 3 things:
- cardinality
- participation
- keys

The following are a exhaustive set of rules that help in constructing proper tables. how to use? Just try to create tables and also satisfy the rules at the same time. The rules get satisfied at a certain point, stop there, you are done.

Steps:
1. Given a ER diagram, find its cardinality and participation values of entities, and then transform the diagram into a table using a general algorithm.
2. Try to store *all* data in tables and make sure all criteria are satisfied.
3. Use set theoretic notation.

Satisfaction criteria:
1. Minimize \# of tables. *Initially try to do it all in one table, if not possible create more tables and check, and continue like so*.
2. Every table must have a primary key. It must be unqiue and not null. *Try to make attributes PK and see if they can be NULL, if yes, consider another attribute for PK. If never null, check if unique*.
3. Each cell must have one value (as opposed to many, i.e. array). The value can be NULL, fine. *Make a relation table or try to create extra columns (if it scales).*

note: 
- I already guessed point 3. Also point 2 makes sense and point 1 in general makes sense, i.e. we don't instantiate tables quickly, nor do we store arrays in a cell (column). Scaling should not be done using these approaches. WHY?
- Generally 3 tables can handle almost everything, since the middle table also has a PK. The usual fight is of disproving 1 is enough, 2 isn't enough.
- Don't worry about both side FK/PKs if the FK is unique (binary search is possible). one side is enough as long as the link exists and all data is captured.


## Constructing table example problems
- Lets try for one-one and partial-partial relation? Can it be done in one table?
	![](../../../../assets/2-Cardinality-of-relationships-and-constructing-minimal-tables-image-3-6718f520.png)
	Not possible, see counter example below
	![](../../../../assets/2-Cardinality-of-relationships-and-constructing-minimal-tables-image-4-6718f520.png)
Note: 
- many-many relations need 3 tables no matter the cardinality.