# Database

* Normalization
  * Suitable for online transaction processing systems (OLTP)
  * 1NF
  * 2NF
  * 3NF
* Denormalization
  * Suitable for online analytical processing systems (OLAP)
* Index
  * Dense vs Sparse Index Files
  * Multilevel Index
  * B-Tree
  * B+-Tree
  * Hash Indicies
  * LSM-Tree
  * R-Tree
  * Bitmap Indices
* CAP Theorem
* Transactions and isolation levels
  * ACID vs BASE
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
