# SQL Server

* Normalization
  * Suitable for online transaction processing systems (OLTP)
  * 1NF
  * 2NF
  * 3NF
* Denormalization
  * Suitable for online analytical processing systems (OLAP)
* Primary-key constraint
  * Enforces the uniqueness of rows and also disallows NULLs in the constraint attributes
  * To enforce the uniqueness of the logical primary-key constraint, SQL Server will create
      a unique index behind the scenes. A unique index is a physical mechanism used by
      SQL Server to enforce uniqueness
* Unique constraint
  * SQL Server will create a unique index behind the scenes as the physical mechanism to enforce
      the logical unique constraint.
  * Two NULLs value were equal to each other
* Foreign-key constraint
* Check constraint
* Default constraint
* Inheritance
  * Table-per-Type
  * Table-per-Hierarchy
* Index
  * Clustered
  * Nonclustered
* Three-Valued predicate logic
* Logical query processing
* All-at-once operations
* Self-Contained sub query
  * Scalar
  * Multivalued
* Correlated sub query
* Table expression
  * Derived table
  * View
  * CTE
    * Recursive CTE
  * Inline table-valued function
* Cross and outer apply operator
* Window functions
  * Ranking
    * ROW_NUMBER
    * RANK
    * DENSE_RANK
    * NTILE
  * Offset
    * LEAD
    * LAG
    * FIRST_VALUE
    * LAST_VALUE
* Inserting data
  * INSERT VALUES
  * INSERT SELECT
  * INSERT EXEC
  * SELECT INTO
  * BULK INSERT
* The identity property and the sequence object
* Deleting data
  * Delete statement
  * Truncate
* Merge statement
* The OUTPUT clause and nested DML
* Transactions and isolation levels
  * ACID property
  * Isolation Levels
    * READ UNCOMMITTED
      * Dirty reads
    * READ COMMITTED
      * *Non-Repeatable Reads* or *Inconsistent Analysis*
    * REPEATABLE READ
      * Prevent phenomenon called a lost update
    * SERIALIZABLE
      * Prevent phenomenon called phantom reads
  * Isolation levels based on row versioning
    * SNAPSHOT
    * READ COMMITTED SNAPSHOT
  * Deadlocks
    * SQL Server chooses to terminate the transaction that did the least work
        (based on the activity written to the transaction log)
    * DEADLOCK_PRIORITY
    * Deadly embrace deadlock
* Temporary tables
  * Local
  * Global
  * Table variable
* Dynamic SQL
  * The *EXEC* command
  * The *sp_executesql* stored procedure
* User-defined functions
  * Scalar
  * table-valued
* Stored procedure
* trigger
  * DML
    * After
      * Permanent tables
    * Instead of
      * Permanent tables
      * Views
  * DDL
    * Database scope
      * For events with a database scope, such as CREATE TABLE
    * Server scope
      * For events with a server scope, such as CREATE DATABASE
    * SQL Server supports only after DDL triggers; it doesn’t support instead of DDL triggers
    * Can be used for
      * Auditing
      * Policy enforcement
      * Change management
