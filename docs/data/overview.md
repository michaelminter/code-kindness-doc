# SQL

## Index Types (Postgres)
Indexes are special lookup tables that need to be used by the database search engine to speed up data retrieval. An index is simply a reference to data in a table. A database index is similar to the index in the back of a journal. It cannot be viewed by the users and just used to speed up the database access.

There are six types of PostgreSQL indexes, which are also called methods, because they define the way each particular index handles its task. They also determine the syntax specifics. These six types are as follows:

- B-Tree
- Hash
- Generalized Inverted Index (GIN)
- Generalized Search Tree (GiST)
- SP-GiST
- Block Range Index (BRIN)

### B-Tree
B-Tree is the default index type for the CREATE INDEX command in PostgreSQL. It is compatible with all data types, and it can be used, for instance, to retrieve NULL values and work with caching. B-Tree is the most common index type, suitable for most cases.

### Hash
Hash is a specific index type applied only if the equality condition = is being used in the query. It is called hash because it stores a 32-bit hash code derived from the indexed column value. Hash indexes are rarely used in PostgreSQL because it is necessary to rebuild them manually after crashes, and they can cause issues during transactions.

### Generalized Inverted Index (GIN)
GIN (Generalized Inverted Index) is suitable for mapping multiple values to one row. The most common case for applying the GIN index comprises operations with data types such as arrays, range types, JSON, and also for full-text search. Note that the GIN index will be slower for INSERT and UPDATE operations.

### Generalized Search Tree (GiST)
The GiST (Generalized Search Tree) index allows using the tree structure to index schemes for new data types—for instance, geometric data types and network address data. GiST is also useful if you have queries that are not indexable with B-Tree. It is applicable for full-text search as well.

### SP-GiST
The SP-GiST (Space-Partitioned GiST) index is similar to GiST, but it uses a partitioned search tree to index non-balanced data structures, thus simplifying the SEARCH and INSERT operations. The common characteristic of these structures is that they repeatedly divide the search space into partitions that do not have to be of the same size.

### Block Range Index (BRIN)
BRIN (Block Range Index) applies to large tables where specific columns have a natural correlation with their physical location in the table. A block range is a group of pages that are physically adjacent in the table; BRIN indexes store summary information—page number along with minimum and maximum values—for each block range.

Only the B-Tree index type does not require any additional specification in the CREATE INDEX statement, as it is the default one in PostgreSQL. To create an index of any other type, you need to specify it – hash, gist, spgist, gin, or brin.

Besides the abovementioned index types, we can single out several index subsets.

### Unique indexes
A unique index makes sure that your table does not have more than one row with the same value. This index type is very helpful when it comes to maintaining data integrity and high performance in PostgreSQL.

### Partial indexes
A partial index is an index with a WHERE clause, which covers a particular subset of data in a table. It is rather small, works faster, and can be used alongside other indexes on more complex queries.

### Expression indexes
Expression indexes are meant for queries matching on a function or modification of data. PostgreSQL makes it possible to index the result of the function and make this search as efficient as search by raw data values.

### Multi-column indexes
An index can be created on more than one table column. In this case, we are dealing with a multi-column index, which is limited to 32 columns (the limit can be changed in pg_config_manual.h). Note that only B-Tree, GIN, GiST, and BRIN types support multi-column indexes.

### When should indexes be avoided?
One more thing before we proceed to the CREATE INDEX command: although indexes are meant to improve database performance, there are cases when they can slow it down and thus should best be avoided:

- You should not use indexes on small tables.
- You should not use indexes on tables that face large and frequent batch UPDATE and INSERT operations.
- You should not use indexes on columns that have many NULL values.
- You should not use indexes on columns that are frequently edited.

## Constraints
Constraints are the rules enforced on data columns on table. These are used to prevent invalid data from being entered into the database. This ensures the accuracy and reliability of the data in the database.

Constraints could be column level or table level. Column level constraints are applied only to one column whereas table level constraints are applied to the whole table. Defining a data type for a column is a constraint in itself. For example, a column of type DATE constrains the column to valid dates.

The following are commonly used constraints available in PostgreSQL.

NOT NULL Constraint : Ensures that a column cannot have NULL value.

UNIQUE Constraint : Ensures that all values in a column are different.

PRIMARY Key : Uniquely identifies each row/record in a database table.

FOREIGN Key : Constrains data based on columns in other tables.

CHECK Constraint : The CHECK constraint ensures that all values in a column satisfy certain conditions.

EXCLUSION Constraint : The EXCLUDE constraint ensures that if any two rows are compared on the specified column(s) or expression(s) using the specified operator(s), not all of these comparisons will return TRUE.

### NOT NULL Constraint
By default, a column can hold NULL values. If you do not want a column to have a NULL value, then you need to define such constraint on this column specifying that NULL is now not allowed for that column. A NOT NULL constraint is always written as a column constraint.

A NULL is not the same as no data; rather, it represents unknown data.

Example
For example, the following PostgreSQL statement creates a new table called COMPANY1 and adds five columns, three of which, ID and NAME and AGE, specify not to accept NULL values −

```sql
CREATE TABLE COMPANY1(
  ID INT PRIMARY KEY     NOT NULL,
  NAME           TEXT    NOT NULL,
  AGE            INT     NOT NULL,
  ADDRESS        CHAR(50),
  SALARY         REAL
);
```

### UNIQUE Constraint
The UNIQUE Constraint prevents two records from having identical values in a particular column. In the COMPANY table, for example, you might want to prevent two or more people from having identical age.

Example
For example, the following PostgreSQL statement creates a new table called COMPANY3 and adds five columns. Here, AGE column is set to UNIQUE, so that you cannot have two records with same age −

```sql
CREATE TABLE COMPANY3(
  ID INT PRIMARY KEY     NOT NULL,
  NAME           TEXT    NOT NULL,
  AGE            INT     NOT NULL UNIQUE,
  ADDRESS        CHAR(50),
  SALARY         REAL    DEFAULT 50000.00
);
```

### PRIMARY KEY Constraint
The PRIMARY KEY constraint uniquely identifies each record in a database table. There can be more UNIQUE columns, but only one primary key in a table. Primary keys are important when designing the database tables. Primary keys are unique ids.

We use them to refer to table rows. Primary keys become foreign keys in other tables, when creating relations among tables. Due to a 'longstanding coding oversight', primary keys can be NULL in SQLite. This is not the case with other databases

A primary key is a field in a table, which uniquely identifies each row/record in a database table. Primary keys must contain unique values. A primary key column cannot have NULL values.

A table can have only one primary key, which may consist of single or multiple fields. When multiple fields are used as a primary key, they are called a composite key.

If a table has a primary key defined on any field(s), then you cannot have two records having the same value of that field(s).

Example
You already have seen various examples above where we have created COMAPNY4 table with ID as primary key −

```sql
CREATE TABLE COMPANY4(
  ID INT PRIMARY KEY     NOT NULL,
  NAME           TEXT    NOT NULL,
  AGE            INT     NOT NULL,
  ADDRESS        CHAR(50),
  SALARY         REAL
);
```

### FOREIGN KEY Constraint
A foreign key constraint specifies that the values in a column (or a group of columns) must match the values appearing in some row of another table. We say this maintains the referential integrity between two related tables. They are called foreign keys because the constraints are foreign; that is, outside the table. Foreign keys are sometimes called a referencing key.

Example
For example, the following PostgreSQL statement creates a new table called COMPANY5 and adds five columns.

```sql
CREATE TABLE COMPANY6(
  ID INT PRIMARY KEY     NOT NULL,
  NAME           TEXT    NOT NULL,
  AGE            INT     NOT NULL,
  ADDRESS        CHAR(50),
  SALARY         REAL
);
```

For example, the following PostgreSQL statement creates a new table called DEPARTMENT1, which adds three columns. The column EMP_ID is the foreign key and references the ID field of the table COMPANY6.

```sql
CREATE TABLE DEPARTMENT1(
  ID INT PRIMARY KEY      NOT NULL,
  DEPT           CHAR(50) NOT NULL,
  EMP_ID         INT      references COMPANY6(ID)
);
```

### CHECK Constraint
The CHECK Constraint enables a condition to check the value being entered into a record. If the condition evaluates to false, the record violates the constraint and is not entered into the table.

Example
For example, the following PostgreSQL statement creates a new table called COMPANY5 and adds five columns. Here, we add a CHECK with SALARY column, so that you cannot have any SALARY as Zero.

```sql
CREATE TABLE COMPANY5(
  ID INT PRIMARY KEY     NOT NULL,
  NAME           TEXT    NOT NULL,
  AGE            INT     NOT NULL,
  ADDRESS        CHAR(50),
  SALARY         REAL    CHECK(SALARY > 0)
);
```

### EXCLUSION Constraint
Exclusion constraints ensure that if any two rows are compared on the specified columns or expressions using the specified operators, at least one of these operator comparisons will return false or null.

Example
For example, the following PostgreSQL statement creates a new table called COMPANY7 and adds five columns. Here, we add an EXCLUDE constraint −

```sql
CREATE TABLE COMPANY7(
  ID INT PRIMARY KEY     NOT NULL,
  NAME           TEXT,
  AGE            INT  ,
  ADDRESS        CHAR(50),
  SALARY         REAL,
  EXCLUDE USING gist
  (NAME WITH =,
  AGE WITH <>)
);
```

Here, USING gist is the type of index to build and use for enforcement.

You need to execute the command CREATE EXTENSION btree_gist, once per database. This will install the btree_gist extension, which defines the exclusion constraints on plain scalar data types.
As we have enforced the age has to be same, let us see this by inserting records to the table −

```sql
INSERT INTO COMPANY7 VALUES(1, 'Paul', 32, 'California', 20000.00 );
INSERT INTO COMPANY7 VALUES(2, 'Paul', 32, 'Texas', 20000.00 );
INSERT INTO COMPANY7 VALUES(3, 'Paul', 42, 'California', 20000.00 );
```

For the first two INSERT statements, the records are added to the COMPANY7 table. For the third INSERT statement, the following error is displayed −

```sql
ERROR:  conflicting key value violates exclusion constraint "company7_name_age_excl"
DETAIL:  Key (name, age)=(Paul, 42) conflicts with existing key (name, age)=(Paul, 32).
```

### Dropping Constraints
To remove a constraint you need to know its name. If the name is known, it is easy to drop. Else, you need to find out the system-generated name. The psql command \d table name can be helpful here. The general syntax is −

```sql
ALTER TABLE table_name DROP CONSTRAINT some_name;
```

## Stored Procedures
A PostgreSQL function or a stored procedure is a set of SQL and procedural commands such as declarations, assignments, loops, flow-of-control etc. stored on the database server and can be involved using the SQL interface. And it is also known as PostgreSQL stored procedures.
