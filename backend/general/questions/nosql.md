# NoSQL

* Explain Polyglot Persistency?
* What's Impedance Mismatch?
* Why choose a NoSQL database?
* How do we choose which NoSQL database?
## Data Models
  * What's the Aggregate Model?
  * What are the Schemaless Databases?
  * What's a Materialized View?
## Distribution Models
  * What types of Data Distribution Models are there?
    * Single Server (No distribution)
    * Sharding
      * Explain Sharding?
      * How does the data being read?
      * How does the data being distributed?
    * Replication
      * Explain Replication?
        * What types of Replication are there?
        * Master-slave Replication
          * Explain Master-slave Replication?
        * Peer-to-peer Replication
          * Explain Peer-to-peer Replication?
      * Quorum
        * What's Quorum? 
        * What is the replication factor?
        * How many nodes need to get consistency?
# Types of NoSQL Databases
  * What types of NoSQL Databases are there?
    * Document databases
      * Name/Explain some Document databases?
        * MongoDB, Terrastore, RavenDB
    * Key-value databases
      * Explain how Key-value databases persist an object?
      * Name/Explain some Graph databases?
        * Redis, Memcached, Couchbase, etc.
    * Column family stores
      * Explain row-oriented and column-oriented databases differences?
      * What is a super-column?
      * Name/Explain some Column-family databases?
        * Cassandra, HBase, etc.
    * Graph databases
      * Name/Explain some Graph databases?
        *  Neo4J, Infinite Graph, OrientDB, or FlockDB
# CAP Theorem
  * Explain CAP Theorem?
  * What's Partition tolerance?
  * How does Availability or Consistency trade-off when partition tolerant occurred?
  * Explain BASE (Basically Available, Soft state, Eventual consistency) and its differences with ACID
# Consistency In Distribution
  * What's Write-write conflict?
  * What's Readwrite conflict?
  * What's Read-Your-Writes consistency?
  * Explain pessimistic and optimistic approaches for maintaining consistency?
  * What is an Inconsistency window?
  * Version stamps
    * How can you detect concurrency conflicts?
    * Version stamps Types
      * What's the Counter stamp?
      * What's the GUID stamp?
      * What's the Hash stamp?
      * What's the Timestamp stamp?
    * Vector stamp
      * How does Vector stamp work and detect conflicts that occurred in distribution?
# Map-Reduce
  * What's Map-Reduce?
  * Explain the Basic flow of map-reduce?
  * What are the Partitioning and Combining phases in map-reduce?
