# 6. Load IMDB data
Created Tue Apr 9, 2024 at 6:11 PM


- IMDB - Download the [file](https://drive.google.com/file/d/1VkbxhqhXtqxlNXUEhlc0Rzl8Rhudjm84/view?usp=sharing)
- W3Schools - loadable into onecompiler - https://github.com/sanjarcode/sample-database/tree/master


Start MySQL in the terminal and run:
```sql
CREATE DATABASE imdb;
USE imdb;
SOURCE path-to-sql-file;
```

This will run the SQL commands of the file in `imdb` database, effectively importing all data.
Takes about 30 seconds (file is ~150MB)