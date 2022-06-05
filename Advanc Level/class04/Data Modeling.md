# NoSQL vs SQL :

## Diferences between SQL and NoSQL:
| SQL                                                                               | NoSQL                                                                                                                   |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| called as Relational Databases (RDBMS)                                            | called as non-relational or distributed database                                                                        |
|  table based databases                                                            | document based, key-value pairs, graph databases or wide-column stores                                                  |
| have predefined schema                                                            | have dynamic schema for unstructured data                                                                               |
| vertically scalable                                                               | horizontally scalable                                                                                                   |
| scaled by increasing the horse-power of the hardware                              | scaled by increasing the databases servers in the pool of resources to reduce the load                                  |
| uses SQL ( structured query language ) for defining and manipulating the data     | focused on collection of documents                                                                                      |
|  examples: MySql, Oracle, Sqlite, Postgres and MS-SQL. NoSQL database             | examples: MongoDB, BigTable, Redis, RavenDb, Cassandra, Hbase, Neo4j and CouchDb                                        |
| good fit for the complex queries                                                  | not good fit for complex queries                                                                                        |
|  not best fit for hierarchical data storage                                       | fits better for the hierarchical data storage as it follows the key-value pair way of storing data similar to JSON data |
| emphasizes on ACID properties ( Atomicity, Consistency, Isolation and Durability) |  follows the Brewers CAP theorem ( Consistency, Availability and Partition tolerance )                                  |
<br>

## SQL Database Examples :
1. MySQL
- MySQL database is very popular open-source database.

- MySQL benefits : 

    - Replication
    - Sharding
    - Memcached as a NoSQL API to MySQL
    - Maturity
    - Wide range of Platforms and Languages
    - Cost effectiveness

2. MS-SQL Server Express Edition : 

- It is a powerful and user friendly database which has good stability, reliability and scalability with support from Microsoft

- MS-SQL benefits and strengths:

    - Integrated Development Environment
    - Disaster Recovery
    - Cloud back-up

3. Oracle Express Edition :

- It is a limited edition of Oracle Enterprise Edition server with certain limitations. This database is free for development and deployment

- Oracle benefits and strengths :

    - Easy to Upgrade
    - Wide platform support
    - Scalability

## NoSQL Database Example :

1. MongoDB :

- Mongodb is one of the most popular document based NoSQL database as it stores data in JSON like documents. It is non-relational database with dynamic schema.

- MongoDB benefits and strengths :

    - Speed: For simple queries, it gives good performance, as all the related data are in single document which eliminates the join operations.
    - Scalability: It is horizontally scalable i.e. you can reduce the workload by increasing the number of servers in your resource pool instead of relying on a stand alone resource.
    - Manageable: It is easy to use for both developers and administrators. This also gives the ability to shard database
    - Dynamic Schema: Its gives you the flexibility to evolve your data schema without modifying the existing data

2. CouchDB

- CouchDB is also a document based NoSQL database. It stores data in form of JSON documents.

 - CouchDB benefits and strengths:
   - Schema-less
    - HTTP query
   - Conflict Resolution
    - Easy Replication

3. Redis

- Redis is another Open Source NoSQL database which is mainly used because of its lightening speed. It is written in ANSI C language.

- Redis benefits and strengths:
    - Data structures
    - Redis as Cache
    - Very fast

# SQL Modeling Techniques :

## Data Modeling – Table Elements
![](https://www.essentialsql.com/wp-content/uploads/2021/11/Database-Table-Data-Modeling.png)

The diagram above shows my method to model a relational database table.  The major elements that are depicted include:

- The Table Name, which is located at the top of the table.
- The Primary Keys.  Remember the primary keys uniquely identify each row in a table.  A table typically has one primary key, but can have more.  When the key has more than one column, it is called a compound key.
- Table Columns – There can be one or more table columns.  To keep the diagrams simple, I don’t show the data types.  I may introduce those later when we focus on more comprehensive modeling.
- Foreign Key – This is a column or set of columns which match a primary key in another table.

## Data Modeling – Table Relationships:
![](https://www.essentialsql.com/wp-content/uploads/2014/06/DataModel-Relations1.png)


### Relations :

**Cardinality ---------- Notation**

zero or one-to-many ---------- 0..*

one-to-many ---------- 1..*

zero or one-to-one ---------- 0..1

one-to-one ---------- 1..1

many-to-many ---------- * .. *

# References

## [NoSQL vs SQL](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool)

## [SQL Modeling Techniques](https://www.essentialsql.com/get-ready-to-learn-sql-7-simplified-data-modeling/)

## [Sequelize API](https://sequelize.org/docs/v6/)
## [Normalization](https://www.essentialsql.com/database-normalization/)



## [Back To Home Page](../../README.md)
