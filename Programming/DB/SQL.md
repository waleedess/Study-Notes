
> SQL (Structured Query Language) is the standard language for creating and working with relational databases. It is usually divided into four components, each with a different job. In short, DDL builds the structure, DML fills and changes the data, DCL controls access, and TCL keeps changes safe.

1. **Data Definition Language - DDL:** Defines the structure of the database. Its commands create, change, and remove tables and other objects. The main commands are `CREATE`, `ALTER`, and `DROP`
2. **Data Manipulation Language - DML:** Works with the data inside the tables. Its commands are `INSERT`, `UPDATE`, and `DELETE`. Many courses also place querying here, using `SELECT`, which some courses treat as a separate component called DQL (Data Query Language)
3. **Data Control Language - DCL:** Controls who can access what. Its commands are `GRANT` and `REVOKE`, which give or remove permissions on tables and other objects
4. **Transaction Control Language - TCL:** Manages groups of operations so they succeed or fail together. Its commands are `COMMIT`, `ROLLBACK`, and `SAVEPOINT`
   
# Relational Model
---

> what a database is in this model, and the ideas of relation, tuple (row: representing single record), attribute (column: representing property that every tuple has), and domain (set of allowed values for an attribute). Schema builds directly on these terms

# Relation Schema
---

> A **relation schema** describes the structure of a table: its name, its attributes (columns), and the domain (allowed data type and values) of each attribute. It describes _what the table looks like_, not the data inside it
   
- The schema is fixed once the table is designed
	- The instance is the set of rows (tuples) present at a given moment, and it changes every time rows are inserted, updated, or deleted

- **Degree** is the number of attributes (Columns)
- **Cardinality** is the number of tuples (rows)

# Keys 
---
1. **`Primary Key`:** The `candidate key` chosen to identify rows. It is unique and cannot contain `NULL`
   
2. **`Candidate key`:** a minimal `superkey`. One of them becomes the `primary key`
   
3. **`Alternate Key`**: candidate key that was not chosen as the `primary key`. It still uniquely identifies rows

4. **`SuperKey`:** any set of attributes that uniquely identifies a tuple. It may include extra attributes that aren’t needed for uniqueness. Can be the full row

5. **`Composite key`:** a key made of two or more attributes together. It can be a `superkey`, `candidate key`, or `primary key`

6. **`Foreign key`:** an attribute that refers to the `primary key` of another relation, enforcing referential integrity

# Constraints 

> Constraints are rules the database enforces on the data in a table. Any insert or update that breaks a rule is rejected, so bad data never gets stored. They’re declared inside `CREATE TABLE`, either next to a column or as a separate line

1. `NOT NULL`
2. `UNIQUE`
3. `PRIMARY KEY`: combines `NOT NULL` and `UNIQUE`, and each table has only one
4. `CHECK`: the value must satisfy a condition
5. `DEFAULT`: the value used when an insert doesn’t provide one
6. `FOREIGN KEY`: the value must match an existing primary key value in the referenced table, which keeps references valid (referential integrity)
