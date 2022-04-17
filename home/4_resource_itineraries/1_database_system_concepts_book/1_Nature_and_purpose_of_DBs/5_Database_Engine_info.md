# 5. Database Engine info
#### Why do we need database engines?
We need database engines for storage and access of data of the database.

#### Components of a database engine
The functional components of a database can be broadly divided into 3:
1. Storage manager - manages storing of database data in parts.
	- Important because database typically require a large amount of storage space - even upto Petabytes (i.e. 1024 Terabytes).
	- As the main memory is almost negligible as compared to the database size, data is stored on disk. Data are moved between main memory and disk as needed.
	- Since the movement of data between main memory and disc is slow, transfers need to be minimized.
2. Query processor - helps the database system to simplify and facilitate access to data.
	- It allows users to work at the view level with good performance while not being burdened by the low level details.
	- Its job is to translate queries and updates written in non-procedural language, at the physical level, into efficient sequence of operations at the physical level.
3. Transaction management component (not manager)
	- Allows application developers to treat a sequence of database accesses as if they were a single atomic access.
	- This permits thinking at a higher level of abstraction about the application without needing to be concerned with the lower-level details of managing the effects of concurrent access to data and of system failures.

- While database engines where traditionally centralized computer systems, today parallel processing is key for handling very large amounts of data efficiently.
- Modern database engines pay a lot of attention to parallel data storage and parallel query processing.

#### Component 1 - Storage manager
- The raw data are stored on the disk using the file system provided by the OS.
- The storage manager is responsible for interaction with the file system. This includes the translation of DML statements into low-level file-system commands. Thus, the storage manager is responsible for storing, retrieving and updating data in the database.
- Components of the storage manager:
	1. Authorization and integrity manager - which tests for the satisfaction of integrity constraints