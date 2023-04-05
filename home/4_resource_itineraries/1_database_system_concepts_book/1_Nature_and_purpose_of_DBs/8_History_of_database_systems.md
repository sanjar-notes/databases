# 8. History of database systems
Created Wednesday 5 April 2023 at 01:08 pm

- Information processing drives growth and use of computers

## 1950s and early 1960s - Magnetic tapes were used for storing data.
  - The primary problem with this was "sequentiality" of reads, writes.
  - The "sequentiality" and slow speeds negatively affected the design of software.
## Late 1960s and early 1970s - hard disks were used for storing data.
  - Sequentiality was no longer a problem, since hard disk practically allowed random access.
  - Reads/write now very fast, allowing for practical storage of relatively complex data structures (such as trees, linked lists) on disk.
  - Relational data model was defined by Edgar Codd in 1970. This led to development of relational databases.
## Late 1970s and 1980s - relational model becomes practical.
  - The relational model was academically interesting, but was not used in practice due to it's perceived performance disadvantages, compared to existing network and hierarchical databases.
  - System R was a project at IBM, that changed this notion, by developing an efficient relational database system.
  - Many commercial database like IBM DB2, Oracle were developed.
  - Declarative queries became practical and popular.
  - Much research on parallel, distributed and object-oriented databases took place.
## 1990s - high performance DBs and the Web. Analysis became common.
  - Due to the Web, databases were deployed more extensively, and expected to support very high transaction-processing rates with very high reliability and availability (24x7)
  - Large scale data analysis saw increased usage.
  - Many vendors started offering parallel databases.
  - Vendors also began adding object-relational support to existing databases.
## 2000s - evolution in types of data. Open-source DBs. Data mining. Data based programming concepts. NoSQL.
  - Semi-structured data became important.
  - XML and JSON storage support was added to existing databases.
  - Open-source DBs like PostgeSQL and MySQL saw increased use.
  - Social networking platform grew, triggering development of graph databases, since tables were not an efficient structure for storing users and connections between them.
  - Data analytics and data mining became ubiquitous, especially in large organizations. "Column-stores" were commonly used in these tasks, instead of traditional row-oriented DBs.
  - Large volumes data and it's semi-structured nature, led to the development of frameworks like map-reduce, to exploit parallelism.
  - The debate for/against using different types of database for OLTP and OLAP became common.
  - Need for rapid development, particularly by startup forms, led to "NoSQL" databases. The freedom from SQL or strict schemas allowed for greater flexibility in app development. NoSQL databases also have the advantage of high availability, high scalability and support very high rate of accesses.
  - "Eventual" consistency became popular, especially in NoSQL database. This is quite relevant to distributed systems.
## 2010s - NoSQL became a little strict. Cloud computing.
  - NoSQL maintenance is hard, for developers. This led to inclusion of some level of strictness and traditional constructs in NoSQL databases.
  - Cloud computing is the de-facto way to run DBs, as well as server apps. This is relatively cheaper, but comes at the cost of security and privacy (if a government requests access data to the cloud provider).
