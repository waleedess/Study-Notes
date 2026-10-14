
> SQL (Structured Query Language) is the standard language for creating and working with relational databases. It is usually divided into four components, each with a different job. In short, DDL builds the structure, DML fills and changes the data, DCL controls access, and TCL keeps changes safe.

1. **Data Definition Language - DDL:** Defines the structure of the database. Its commands create, change, and remove tables and other objects. The main commands are `CREATE`, `ALTER`, and `DROP`
2. **Data Manipulation Language - DML:** Works with the data inside the tables. Its commands are `INSERT`, `UPDATE`, and `DELETE`. Many courses also place querying here, using `SELECT`, which some courses treat as a separate component called DQL (Data Query Language)
3. **Data Control Language - DCL:** Controls who can access what. Its commands are `GRANT` and `REVOKE`, which give or remove permissions on tables and other objects
4. **Transaction Control Language - TCL:** Manages groups of operations so they succeed or fail together. Its commands are `COMMIT`, `ROLLBACK`, and `SAVEPOINT`
   
# Relational Model
---

> what a database is in this model, and the ideas of relation, tuple (row), attribute (column), and domain. Schema builds directly on these terms

# Relation Schema
---

> A **relation schema** describes the structure of a table: its name, its attributes (columns), and the domain (allowed data type and values) of each attribute. It describes _what the table looks like_, not the data inside it
   
   
   