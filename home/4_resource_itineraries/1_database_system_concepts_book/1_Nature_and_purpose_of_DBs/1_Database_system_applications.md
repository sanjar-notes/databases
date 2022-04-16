# 1. Database system applications
- [ ] in vault

#### History
- The first use of database was in the 1960s, when office data was commercialized.
- Data means much of the value of today's companies, as compared to their physical assets. Example - banks, social media services, e-commerce stores.
- Databases and the data they contain has become flexible over time, as compared to the 1960s, where they were precisely structured.

#### When to use a database
Database systems are used to manage collections of data that are:
1. Highly valuable
2. Relatively Large
3. Accessed by multiple users and apps, often at the same time.

#### 2 Modes of database use
There are two modes in which databases are used:
1. Online transaction processing - these types of DBs have many users, who update very small amounts of data. This is also known as OLTP.
2. Data analytics or OLAP (Online Analytical Processing) - historical data is used to draw conclusions, infer rules and drive business decisions. Example - data mining using AI and statistical analysis on very large databases.

#### Purpose of Database Systems
Why do we need database systems, aren't file systems enough?

No, file systems are not enough, because of the following reasons:
1. Difficulty in accessing data: Quering would mean writing a program each time, which is quite inefficient.
2. Migration: Structure of the data would be difficult to change if rules of the domain changed.
3. Data redundancy and inconsistency - because related files are not connected/watched over by a program continually, data in them could become inconsistent. Example - A student changed his name, but the data was changed at the most relevant place, and not all the places. Redundancy also increases cost, both physical and computational.
4. Data formats for the same data may be different for different file, and it'd be very difficult to write programs for different file formats.
5. Concurrent access anomalies.
6. Atomicity problems - an action on the system must either take place fully, or it must leave the system as is. This is difficult to do with a file system (TODO: why?).
7. Security (authorization) - not all parts of the system must be available to all stakeholders, and this is difficult to enforce in a file system because the access programs are written in an ad-hoc manner.