---
id: 603d252d-91ec-4f35-950e-26211cd5112a
title: Ch07 - Transactions
desc: ''
updated: 1614537039718
created: 1604290478828
---
# Chapter 7: Transactions 

Purpose of transactions: simplify the programming model

## ACID definition is slippery

- Atomicity:
    - different from normal meaning in concurrency programming (nobody else sees a partially updated state)
    - means more _abortability_ - when  failure, all partial updates are reverted 
- Consistency: 
    - overloaded term
    - means some _invariants_ to be true - but it's more up to application. 
    - 'C' doesn't really belong
- Isolation:
    - concurrently executing transactions are isolated from each other: they cannot step on each other’s toes
    - i.e. _serializability_ - result is the same as if they had run serially
    - in practice, **strictly serializable isolation is rarely used**. Oracle 11g doesn’t even implement it.
- Durability
    - once committed, data written is stored 
        - persisted to disk in single node
        - or replicated in multi-node

### single-object vs multi

- Atomicity and isolation apply both to single and multi-object
    - on single object:
        - almost universally provided 
            - Atomicity - log for crash recovery 
            - isolation - a lock on each object 
        - some provide atomic operations e.g. increment or compare-and-et 
    - multi-object:
        - in relational model, foreign key constraints to other table has to be met 
        - in document, need transactions to prevent denormalized data going out of sync 
        - update sconedary indexes 
- handling error
    - ACID databases abandon transactino entirely if at risk of ACID
    - quorum storage - "best "effort" 


## Weak Isolation Levels 

Serializable isolation has a performance cost, and many databases - including **many popular relational DBs** don’t want to pay that price. 

### Read Committed
- when reading, only see committed data - **no dirty reads**
- when writing, only overwrite data that has been fully committed  - **no dirty writes**
- very popular - deulat in Oracle 11g, PostgreSQL, SQL Server 2012 etc.
- implementation
    - prevent dirty writes by row level locks 
    - prevent dirty reads: not by read locks, but by **keeping the old commited value and the new value set by the transaction that currently holds the write lock**.

### Snapshot Isolation and Repeatable Read

- reads might see effect of part of the transaction 
- use case where it's important and useful: **long-running, read-only queries**
    - backup 
    - Analytic queries and integrity checks
- Snapshot Isolation: each transaction reads from a consistent snapshot of the database
- Implementation
    - prevent dirty writes by locks
    - no read locks - instead, keep several different committed versions of an object - **multi-version concurrency control (MVCC)**.
        - always-increasing transaction ID
            ![](/assets/images/2020-11-11-22-47-29.png)
        - when reading, only read the latest committed version of the row with write tx id < read tx id 
    - **Indexes** 
        - option 1: index simply point to all versions of an object, filter at read time
        - option 2: (PostgreSQL) avoid index updates if diff version on the same page
        - option 3: append-only B-trees - updates generate a new page. all parents up to root is copied and updated to new.  a particular root is a consistent snapshot of the database at the point in time when it was created. require background compaction and garbage collection. 
        
- naming confusion
    - different DB call it differently, and actual guarantees are different 
    - because SQL standard has flawed defintion for **repeatable read** - 