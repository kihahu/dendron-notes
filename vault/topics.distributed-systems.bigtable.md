---
id: 70076aa3-4564-4d29-8559-c766fa201698
title: Google BigTable
desc: ''
updated: 1605477154833
created: 1605474602967
---

# Google BigTable
- Bigtable: A Distributed Storage System for Structured Data (https://research.google/pubs/pub27898/)
- hosted on GCP: Cloud Bigtable
- Inspired **Apache Cassandra** (from Facebook)
- **Spanner** is layered on top 

## Logical data model

![](/assets/images/2020-11-15-16-23-55.png)

- Key (row:string, column:string, time:int64) → Value: string
- Row: 
    - data stored in **lexicographic order by row key**
    - row range = **_tablet_**
    - when storing URLs, use reversed URL as row ID so URLs from the same domain are close to each other: `com.google.maps`  `com.google.images`
- Column Families
    -  Colume key: `family:qualifier`
- Timestamps
    - multiple versions of data 
    - garbage-collect rules:
        - \# of versions to keep
        - discard versions older than x days
    
## API 

- Write - atomic operation on rows - supports single-row transactions 
    ```C++
    Table *T = OpenOrDie("/bigtable/web/webtable");
    // Write a new anchor and delete an old anchor
    RowMutation r1(T, "com.cnn.www"); 
    r1.Set("anchor:www.c-span.org", "CNN"); 
    r1.Delete("anchor:www.abc.com");
    Operation op;
    Apply(&op, &r1);
    ```
- Read - Clients can iterate over multiple column families for a row 
    ```C++
    Scanner scanner(T);
    ScanStream *stream;
    stream = scanner.FetchColumnFamily("anchor"); 
    stream->SetReturnAllVersions(); 
    scanner.Lookup("com.cnn.www");
    for (; !stream->Done(); stream->Next()) {
        printf("%s %s %lld %s\n", scanner.RowName(), stream->ColumnName(),stream->MicroTimestamp(), stream->Value());

    ```

## Implementation

- master:
    - assign tablets to tablet servers
    - detecting the addition and expiration of tablet servers
    - balancing tablet-server load
    - GFS garbage collection
- tablet servers:
    - 100-200 MB each by default
        ![](/assets/images/2020-11-15-16-39-50.png)
    - tablet server holds an exclusive lock in Chubby 
    - master detect by asking each tablet server for lock status 
        - if fails, master attempts to aquire the server lock. if success, delete the server file, and move assgiment to other tablets 
        - master failure does not change assigment 
    - master at startup:
        - takes a master lock 
        - scan server directory in Chubby
        - contact tablet to learn current assigments 
        - reads METADATA to find tablets 
        - assign un-assigned tablets 
        


![](/assets/images/2020-11-15-16-10-05.png) 
- image from [Youtube: 深入浅出BigTable
](https://www.youtube.com/watch?v=r1bh90_8dsg)