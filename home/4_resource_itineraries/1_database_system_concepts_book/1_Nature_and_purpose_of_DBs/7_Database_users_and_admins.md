# 7. Database users and admins
Created Wednesday 5 April 2023 at 12:47 pm

## Users and interfaces
There are 4 types of users, usually:
1. "Naive" users - unsophisticated users who interact with the database indirectly, usually via web/mobile apps.
2. App programmers - computer professional who write apps. They interact via SQL, but it's not commonly the case. Even if they do, it's more about DML ops instead of DDL ops.
3. Analysts - these are people who are important for an app, but are not involved with the app code - frontend or backend. They usually create data based solutions, which are used in apps. They interact with the DB by using SQL or other software tools, but the nature of queries is "exploratory" rather than for a direct client task.
4. Admins (aka DBA). They:
	- Set up the database, including low-level DB setup if any.
	- Perform DDL ops, like creating the DB from schema definitions provided to them.
	- They alter the database in case of schema changes.
	- Set up authorization
	- Do routine maintenance - backups, ensure free disk space, monitor health (to recognize and mitigate attacks)

Note: 
- Cloud computing - due to the explosion of cloud computing, these roles are getting blurry, especially among programmers/admins (both are usually handled by the same person, nowadays).
- Observability software - are making traditional DBA work easier (in a way). These are software tools, usually in the context of cloud computing, that help in monitoring health of the app infrastructure, including early warning and attack detection capabilities.
- Small vs large companies - small companies, usually startups with limited resources, don't have specialized roles for programmers/analysts/admins. Large and established companies, usually do have these roles - since the scale and risk involved with data they have is larger.