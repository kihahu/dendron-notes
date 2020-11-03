---
id: 603d252d-91ec-4f35-950e-26211cd5112a
title: Ch7 - Transactions
desc: ''
updated: 1604364576549
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


