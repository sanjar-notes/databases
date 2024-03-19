# 2. Why not simply use files Files vs DBMS
Created Tue Mar 19, 2024 at 8:38 AM

In programming languages we have fopen, fprintf, fscanf etc, why aren't these enough to store data?

In other words, why isn't the file system enough for data storage?

- Well, even the DBMS software uses files, at the end of the day.

But a DBMS takes care of many of the details of data, that would have been a lot of effort and non-reliable if a file system was use.

- Also a DBMS can do everything a filesystem can, but the filesystem cannot do everything a DBMS can.