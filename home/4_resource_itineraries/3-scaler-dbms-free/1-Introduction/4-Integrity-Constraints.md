# 4. Integrity Constraints
Created Fri Mar 22, 2024 at 7:27 AM

Integrity constraints are rules that must always be satisfied throughout the database (i.e. all tables), at all times, for the system to be considered "consistent". Being "consistent" is usually a strict minimum requirement.

The advantage and use of these rules is that they avoid inconsistencies and also promote a logical and simple structure.

The rules to satisfy are:
1. Entity integrity - every table must have a primary key, and the key must be unique and not null. btw, FKs may be null or duplicated.
2. Domain integrity - the set of all possible values an attribute can have, i.e. domain. The rule is that this must be defined and known.
3. User-defined integrity - constraints relating to business logic of the app/system that the db is being used for. From a math perspective these are arbitrary. Example: Amazon purchases table where product count has a max limit of 4, to avoid "by-all-and-resell-elsewhere" problem. aka 'CHECK constraint'
4. Referential integrity - related to foreign keys. It's a set of rules (assume two tables - referencing and referenced):
	1. Insert op in referenced table - inherently safe. Nothing to check/do here.
	2. Delete op in referenced table. Then a change must happen in the referencing table. Possibilities:
		1. ON DELETE NO ACTION. Let the row be. integrity broken but fine. This is dangerous because integrity violated. not widely used.
		2. ON DELETE CASCADE. Delete the row in referencing table, and cascade changes further (if referencing table itself has a PK that is an FK elsewhere). This is dangerous because data loss. not widely used.
		3. ON DELETE SET NULL. Let the row in referencing table be. But make FK value null. This is safe because there's no data loss and integrity is preserved. *Widely used.*
	3. Edit op in referenced table. Suppose PK row (that is FK row) is changed, then options are:
		1. ON EDIT NO ACTION - dangerous coz violate integrity. not widely used.
		2. ON EDIT CASCADE - this is *widely used*. Disadvantage - can be time consuming due to cascading ops.
		3. ON EDIT SET NULL - not widely used.
		   
			This is relevant only if you edit PK in referenced table. If not, then this is not an issue.
	4. Insert op in referencing table - check whether FK value (if inserted) exists in referenced table. If not, raise error.
	5. Delete op in referencing table - safe op, do nothing in referenced table(s), including if self referential. There may be ops if the referencing table is a referenced table for some other relation (aka table), but this is not in scope among the given two tables, current and this.
	6. Edit op in referencing table - check for violations in the above rules for other tables.