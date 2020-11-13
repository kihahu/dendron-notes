---
id: c61cfa31-05a8-47de-897d-0fbd0a884e69
title: Ch06 - Partitioning
desc: ''
updated: 1605303416437
created: 1604287587873
---

- Partitioned databases were pioneered in the 1980s by products such as Teradata, rediscvoered by noSQL

## Partitioning by Key Range

- used by BigTable, open source equivalent HBase, MongoDB before v2.4 
- sorted in each partition: range scanes are easy 
- con: hot spots

## partition by hash key 
- choice of hash key: 
    - Cassandra and MongoDB use MD5, Vodemort uses Fowler– Noll–Vo function.
    - MurmurHash -  non-cryptographic but lightweight
    - built-in Java hash function is bad, because same key -> different hash
        - it's built for in memory hash tables and the behavior is [a safety mechanism to prevent collding hash attacks](http://martin.kleppmann.com/2012/06/18/java-hashcode-unsafe-for-distributed-systems.html)
- Consistent Hashing
    - great for caches
    - does not work great for DBs 
- range query difficult - Cassandra and DynamoDB uses hash + sort ey 
- hotspot relief: application level  -  route writes to multiple keys: key_random_num

## Secondary Indexes 

* local index - scatter writes, gather for eads 
    - Used by MongoDB, Riak, Cassandra, Elasticsearch, SolrCloud, and VoltDB 
* global index
    - write reaches multiple partitions - distributed transaction or async update 
    
## Rebalancing Partitions 

1. Fixed number of partitions
    - more partitions than nodes
    - when new node join, steal partitions from others 
    - Used in Riak,  Elasticsearch, Couchbase, and Voldemort 
    - hard to pick the right number of partitions 
    
1. parition spliting and merging 
1. \# of partition proportionally to nodes
    - when a new node joins the cluster, it randomly chooses a fixed number of existing partitions to split, and then takes ownership of half of each partition
    - used by Cassandra
- auto vs manual rebalancing
    - full automation can be dangerous in combination with automatic failure detection

## Request Routing

- require consensus
    - use zookeeper - HBase, SolrCloud, Kafka, Espresso
    - gossip - Cassandra and Riak
    - no autobalancing, routing tier - couchbase 
    
