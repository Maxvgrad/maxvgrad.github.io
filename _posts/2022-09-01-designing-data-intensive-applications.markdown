---
title:  "Designing data intensive applications"
date:   2022-11-04 21:18:58 +0200
categories: book-review
---

Book notes

# Book notes

# Part 1

Chapter 1: Reliable, Scalable, and Maintainable Applications

Many applications today are data-intensive, as opposed to compute-intensive.
What is the limiting factor for modern applications?

Systems like databases, queues and caches are essentially the same applications, which can be called DATA SYSTEMS.

Why do we have variety of tools?
databases like redis can be used as queue and queue like kafka can be used as DB
different tools per different usecase, application code is stitches between tools

Reliability

Ability to work correctly even if things go worng. We can't tolerate all kind of errors, so it should be specified.
Distinguish between fault and failure. Failure when system stop working as a whole.

Difference between fault prevention and fault tolerance. Either or is preferable depending on the usecase. Prevention is beter when there's no cure for the fault.

Three types of errors:
Harware
Software
Humans

How reliability is important? Well think of user who would lose all the data because of the failure. Sometimes it worth sucrifice reliability to reduce costs.

Scalability

Scalability is the term we use to describe a system’s ability to cope with increasedload.


scalability means considering questions like “If the system grows in a particular way,what are our options for coping with the growth?” and “How can we add computing resources to handle the additional load?”


Before improving scalability you need to define load parameters. Something which is important for your system (RPS, ration read/write to db, number of users etc)


Example from Twitter. Estimation of writes and reads between two approaches. Consider order of magnitude.


After load


The difference between response time and latency. Latency is time while the request is latent, waiting to be processed (e.g. batch processing).

An architecture that scales well for a particular application is built around assump‐tions of which operations will be common and which will be rare—the load parame‐ters.

In an early-stage startup or an unpro‐ven product it’s usually more important to be able to iterate quickly on product fea‐tures than it is to scale to some hypothetical future load.


Maintainability

Oprability
Simplicity
Evolvability


Chapter 2: Data Models and Query Languages

For each layer, the key question is: how is it represented in terms of the next-lower layer

Ch 2.1: Relational Model Versus Document Mode
each relation is an unordered collection of tuples (rows in SQL). Initially it was a dominance of traditional relational DBs.

The Birth of NoSQL

driving forces behind the adoption of NoSQL databases
greater scalability, including very large datasets or very high write throughput
preference for free and open source software
Specialized query operations
restrictiveness of relational schemas, and a desire for a more dynamic and expressive data model

The Object-Relational Mismatch
The disconnect between the models is sometimes called an impedance mismatch.
One-to-many seems easy to store as JSON. Better locality, no need to join tables.

Many-to-One and Many-to-Many Relationships
Author is saying that many-to-many is essential relationship for some features like school autocompleter, which is quite difficult to implement if you're using a join-free document.
letting users choose from a drop-down list or autocompleter
Consistent style and spelling
Avoiding ambiguity
Ease of updating
Localization support
Better search
Many-to-one is fairly simple in a document DB, however the relationship doesn't have same benefits as many-to-many.

Replacing meaningful (e.g. "PhD") data with ID is the key idea behind normalization in databases.

Are Document Databases Repeating History?
The problem of NoSql problem to represent dependencies was long time ago before SQL. Two models was suggested to resolve the problem.
Models
relational
network (Conference on Data Systems Languages (CODASYL))

Network - something like liked structure.
Relational is a collection of tuples. The benefit it has a query oprimizer, which works separatly from query itself, so it's easy to change application by providing a different index without changing a query.

If you don’t have a query opti‐
mizer, it’s easier to handcode the access paths for a particular query than to write a
general-purpose optimizer—but the general-purpose solution wins in the long run.

Good point, it's easier to hardcode then write a general purpose solution.

Relational Versus Document Databases Today
Discussion pros cons between relational and document modals.
Application code is more complicated in relational, but if your modal requires joins and you have a document model, then application code still would be complicated. I would say simplifing an application code is not the main goal when you need to choose a DB model, rather investigate what's your data.
Document model is good to represent one-to-many relationship, but the whole document is loaded in memory. Access path includes document ID e.g. get position index 2 for document user 241.
Relational is good for many-to-manh and many-to-one relationships, but it complicates the application code.
Schmal. schema-on-read (document), schema-on-write (relational) . heterogeneous data when it has different format/types.
NB! Update table takes time, because you need to change every record in DB
Data locality, mentioned in general that locality is good. Quite interesting point that document can be rewriten and updated if the size of the document doesn't change.
In the last point, relational DBs support JSON data type and some document DBs support joins, so those two became more similar (hybrids).


Ch 2.2: Query Languages for Data
Each data model comes with it's own query langaage, that's it was discussed.
Discussion abou imperative and declarative language. SQL, CSS are declarative language, you define the outcome, the actual work is done by DB or browser.
Talk about MapReduce and that it's half decalarative and half imperative language.

Ch 2.3: Graph-Like Data Models

## Chapter 1

Scalability is the term we use to describe a system’s ability to cope with increased load.

scalability means considering questions like “If the system grows in a particular way,what are our options for coping with the growth?” and “How can we add computingresources to handle the additional load?”

Before improving scalability you need to define load parameters. Something which is important for your system (RPS, ration read/write to db, number of users etc)

Example from Twitter. Estimation of writes and reads between two approaches. Consider order of magnitude.

### After load

The difference between response time and latency. Latency is time while the request is latent, waiting to be processed (e.g. batch processing).

An architecture that scales well for a particular application is built around assump‐tions of which operations will be common and which will be rare—the load parame‐ters.

In an early-stage startup or an unpro‐ven product it’s usually more important to be able to iterate quickly on product fea‐tures than it is to scale to some hypothetical future load.

## Chapter 3 Storage and Retrieval

Db can be optimised for transactional load or analytics.

They're two db engines:

- Log based
- Page based (B trees)

Discussion about data structure powers DB .

Without index search is O(n). Index speeds up search but shows down insert, because you ~~~~have to write in index.

**Hash Indexes**

Example about bitcask DB. Log based DB.

**B trees**

Most databases can fit into a B-tree that is three or four levelsdeep, so you don’t need to follow many page references to find the page you are look‐ing for. (A four-level tree of 4 KB pages with a branching factor of 500 can store up to256 TB.). How to calculate?

1 terabyte = 2^40 bytes

B tree overwrites pages on disk, to prevent corrupted data DB has a write ahead log WAL.

What's the block size of SSD drive?

DB uses latches to organize concurrency.

**Pros and cons for lam indexes**

+ Lower write amplification

+ Less fragmentation

- compaction can eat DB performance

- compaction might not be able to keep up with writes

**Other indexes**

Secondary index when key can have multiple values. We can associate key with list of values or combine key with unique piece of data like row number.

Clustered index when row stored in the index, it's needed to prevent hop from index leaf to disk (heap file)

Multicolumn index, e.g. phone book last name plus first name.

For example, PostGIS implementsgeospatial indexes as R-trees using PostgreSQL’s Generalized Search Tree indexingfacility [35]. We don’t have space to describe R-trees in detail here, but there is plentyof literature on them.

Fuzzy index when there's no dedicated row. E.g. key can address multiple rows and each row can be a result of search.

In Memory database. All data is loaded in ram. RAM getting cheaper and there are solutions to make data durable.

Why in memory DB has higher performance?

Not only because all the data in RAM but also because in memory it's easy to implement a complex data structure (set or priority queue).

For example,Redis offers a database-like interface to various data structures such as priorityqueues and sets. Because it keeps all data in memory, its implementation is compara‐tively simple.

### Transaction Processing or Analytics?

Access pattern:

- Online transaction processing (OLTP)
- Online analytics processing (OLAP)
- Online analytics processing (OLAP)

Analytics DB has star or snowflake schema. Fact table is in the center and dimension tables around (transfer (fact), user, profile). Snowflake schema is more normalized, it has sub dimensions.

**Star and snowflake ❄️ scheme**

Fact table and dimension tables. Snowflake is more normalized, it has sub dimension tables.

**Column oriented storage**

??? Bitmap

???

However, that is not theonly bottleneck. Developers of analytical databases also worry about efficiently usingthe bandwidth from main memory into the CPU cache, avoiding branch mispredic‐tions and bubbles in the CPU instruction processing pipeline, and making use ofsingle-instruction-multi-data (SIMD) instructions in modern CPUs

Operators, such as the bitwise AND and OR described previously, can bedesigned to operate on such chunks of compressed column data directly. This techni‐que is known as vectorized processing

Summary

when your queries require sequentially scan‐ning across a large number of rows, indexes are much less relevant. Instead itbecomes important to encode data very compactly, to minimize the amount of datathat the query needs to read from disk.
