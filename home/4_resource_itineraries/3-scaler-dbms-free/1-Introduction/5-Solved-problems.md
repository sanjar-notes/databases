# 5. Solved problems
Created Fri Mar 22, 2024 at 7:56 AM

Introduction section's problems

Q1. Given table R(A1, A2, A3, ... An). 
a. Number of super keys if candidate keys are {A1}. Answer: 2<sup>n-1</sup>
b. Number of super keys if candidate keys are {A1, A2}. Answer: 3 \* 2<sup>n-2</sup>
c. Number of super keys if candidate keys are {{A1, A2}, {A3, A4}}. Answer: 3 \* 2<sup>n-4</sup>
d. Number of super keys if candidate keys are {{A1, A2}, {A2, A4}}. Answer: 3 \* 2<sup>n-3</sup>
e. Number of super keys if candidate keys are {{A1, A2, A3}}. Answer: 7 \* 2<sup>n-3</sup>
	![](../../../../assets/5-Solved-problems-image-1-7e7cb3c7.png)

Q2. Given a relation with n attributes, how many superkeys can be present. A: no candidate key. 2<sup>n</sup> - 1. -1 because null set cannot be a super key.