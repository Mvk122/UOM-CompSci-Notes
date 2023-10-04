## Key Value Stores i.e redis
![[Redis_Logo.svg.png]]
* Stores data with keys and values.
* Limited in scope but can be very fast especially if stored completely in memory eg redis.

### When to use
* `As a Cache`: Due to it being in memory, it can be used to store frequently accessed data.
* `Write Oriented`: It has high speed data writes hence can be used in cases like real-time analytics.
* `Message Queue`: Due to it having fast writes and reads, it can be used as a pub/sub message queue.

### Pros
* `Very fast`: Both reads and writes are extremely fast.
* `Simplicity`: Simple data types and a simple conceptual model make it easy to use.

### Cons
* `Not Persistent`: By default, redis is completely in-memory, making data storage not persistent. It can write to a persistent data store however this comes at the cost of speed. This persistence model is also not durable especially during failovers.
* `Limited Query Capabilities`: Due to it only being a key value store, querying complex relationships is not possible/ very difficult.
* `Redundant Data`: Due to not having a schema, there can be redundant data stored.

## Wide Column Databases i.e CassandraDB
![[Cassandra.svg]]
* Like relational databases except the columns and types of data that each row has can vary.
* I.e all rows in a user field can have their name and e-mail but in column oriented databases, a user can also have a favorite color column that no other user has.
* Each column is stored separately eg all e-mail addresses are stored in 1 column.

### When to use
* `Write Oriented` Writing to the database is much faster than reading.
* `Flexible Schema`: Each row can have different columns.
* `Time Series Data`: Create a new column for each timestamp in a row.
### Pros
* `Decentralized` and can scale horizontally. (A row can be on any machine).
* `Replication` is easy as the data can be stored on many machines.
*  `Tunable Consistency`: The amount of consistency can be changed over time.
### Cons
* `Complex Queries`. Complex queries are slow and not guaranteed as each row can have different columns.
* `No ACID`: CassandraDB uses a `BASE` model instead of acid.

## Document Oriented Database i.e MongoDB
![[MongoDB_Logo.svg.png]]
* Each document is a container for key value pairs stored in either JSON or BSON. (Can be thought of as each document being a JSON file).
* It is schemaless and each document can have any number of key value pairs.
* It allows for some structure as documents can refer to the IDs of other documents via One-To-Many or Many-To-Many relationships.
* Uses an `Eventual Consistency` model.

### When To Use
* `Flexible Schema`: Each document can have its own distinct key value pairs.
* `Complex Queries`: Though it does not support queries as complex as SQL databases, documents being able to point to one another allows for some relational hierarchy.
* `More reads than writes`: Reading is very fast but due to a lack of strict relational data, writing data can be more complicated.
* `Writing unrelated data`: If creating documents with no relations to other documents, writes can be extremely fast due to a lack of ACID guarantee.

### Pros
* `Horizontal scaling` is extremely easy as each document can be stored on any node. Automatic sharding further helps in this.
* `Nested Data`: Nested data can be easily stored and queried, reducing the need for joins. 

### Cons
* `Complex Queries`: Though it supports complex queries, a lack of joins and a loose data model makes queries inconsistent and less performant.
* `Not ACID`: Uses eventual consistency.
* `Slow with related data`: Writing related data can be very slow due to the loose data model hence it will be very slow when using highly related data with many writes. A `graph database` would be better for this.

## Relational Databases I.E PostgreSQL
![[ECX-1909_Hero_PostgreSQL_600x400@2x.png]]
* Stores data in tables that all have the same columns.
* Each row has a primary key and this can be referenced in other rows via foreign key relations, allowing for `One to Many`, `Many to One` or `Many to Many` relationships.
* It is `ACID`: 
	* `Atomicity`: Transactions cannot be further divided, hence they either fail or succeed entirely.
	* `Consistency Preservation`: Transactions take the database from one consistent state to another.
	* `Isolation`: Transactions appear as if they are working in isolation.
	* `Durability`: Changes made by a transaction must not be lost due to a failure.

### When to use
* `Complex Relationships`: Relational databases are the best for storing and querying data that has complex relations.
* `ACID`: It is ACID instead of base, providing consistent reliable transactions. 

### Pros
* `Maturity`: Relational databases and SQL are some of the oldest database technologies hence there will be matured integrations for all data types and use cases.
* `Querying`: SQL is a very powerful language and supports joins, making querying data very easy.
* `Data Integrity`: Acid compliance and foreign key constraints ensure data integrity as defined by the user.
* `Low redundancy`: Database normalisation ensures that there is low redundancy, reducing the amount of space data takes up.

### Cons
* `Scalability`: Scaling relational databases is hard and usually constrained to vertical scaling.
* `Rigid Schema`: Making changes to the schema can be difficult and require application downtime. Furthermore, all rows in a table need to have the same columns, making data that is unique per row difficult.
* `Performance Overhead`: It can be slow compared to other databases due to requiring features like ACID compliance.