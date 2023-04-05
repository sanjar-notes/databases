# 6. Database and application architecture
18 April 2022
- [ ] in vault

## Database architecture
This is a layered system.
Layers: User (role) <--> interface (app | server app | SQL (DML only) | SQL) <--> query processor <--> storage manager <--> HW

![](/assets/6_Database_and_application_architecture-image-1.png)

## Application architecture
Based on the layers discussed above, apps that use a DB can be classified into two architectures:
- 2-tier - rare, used for B2B or developers. Was more prevalent in the past. Low security and low performance, but cheap to set up.
- 3-tier - almost always used for B2C apps. Example - web apps, mobile apps. High security and performance(FIXME why? is it because queries are of fixed types, and so, can be optimized in the backend app), but costly to set up.

![](/assets/6_Database_and_application_architecture-image-2.png)

