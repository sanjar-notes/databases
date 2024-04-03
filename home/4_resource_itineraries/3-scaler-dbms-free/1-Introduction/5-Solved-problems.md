# 5. Solved problems
Created Fri Mar 22, 2024 at 7:56 AM

Introduction section's problems

Q1. Given table R(A1, A2, A3, ... An).
a. Number of super keys if candidate keys are {A1}. Answer: 2<sup>n-1</sup>
b. Number of super keys if candidate keys are {A1, A2}. Answer: 3 \* 2<sup>n-2</sup>
c. Number of super keys if candidate keys are {{A1, A2}, {A3, A4}}. Answer: 3 \* 2<sup>n-4</sup>
d. Number of super keys if candidate keys are {{A1, A2}, {A2, A4}}. Answer: 3 \* 2<sup>n-3</sup>
e. Number of super keys if candidate keys are {A1, A2, A3}. Answer: 7 \* 2<sup>n-3</sup>
	![](../../../../assets/5-Solved-problems-image-1-7e7cb3c7.png)

Q2. Given a relation with n attributes, how many superkeys can be present. A: no candidate key. 2<sup>n</sup> - 1. -1 because null set cannot be a super key.


## Challenge
1. ✅ What is a disadvantage of using files over a database management system (DBMS)?
   - [ ] Files provide faster data retrieval compared to DBMS
   - [ ] Files offer better data security than DBMS
   - [x] Files lack data consistency and can lead to data redundancy
   - [ ] Files are easier to maintain and update than DBMS
2. ✅ What is the purpose of primary keys in a database table?
   - [ ] Primary keys uniquely identify a table in the database
   - [ ] Primary keys establish relationships between multiple tables
   - [x] Primary keys ensure data integrity and enforce uniqueness in a table
   - [ ] Primary keys define the data type of each column in a table
3. ❌ Which of the following is an example of an integrity constraint in a database?
   - [x] CHECK constraint
   - [ ] JOIN constraint
   - [ ] INDEX constraint
   - [ ] FOREIGN KEY constraint ✅
4. ✅ What is the purpose of solving problems in a database course?
   - [ ] To improve programming skills
   - [x] To demonstrate database concepts in real-world scenarios
   - [ ] To optimize database performance
   - [ ] To compare different database management systems
