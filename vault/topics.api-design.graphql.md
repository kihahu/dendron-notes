---
id: 3bf41e97-8aeb-4462-bb76-168cebb241b4
title: Graphql
desc: ''
updated: 1614537039731
created: 1606145715534
---


## challenges
- monitoring
    - partial successes 
    - no easy error code like HTTP -> track \#of exceptions 

- Query complexity (can have pathologically nested queries)
    1. only allow cached queries (persisted queries)
    1. calculate complexity score 
    1. calculate query depth
- caching complexity 
    1. Data loader
    1. client side caching

### GraphQL @ Twitter
- [Rebuilding Twitter’s public API
](https://blog.twitter.com/engineering/en_us/topics/infrastructure/2020/rebuild_twitter_public_api_2020.html)

- [GraphQL 2017 summit notes on GraphQL @ Twitter](https://about.sourcegraph.com/graphql/graphql-at-twitter/)
    - authN handled by a layer before GraphQL. authZ handled by  lower-level services. the GraphQL API itself no auth responsibility
        ![](/assets/images/2020-11-23-14-51-17.png)
    - implementing subscriptions with existing internal event bus
        ![](/assets/images/2020-11-23-14-57-50.png)
    - Strato: internal tech. a virtual database, aka federated database, brings together multiple data sources so they can be queried and mutated uniformly
    - 
### GraphQL Federation @Netflix 
notes from 11/23/2020
- [How Netflix Scales its API with GraphQL Federation (Part 1)](https://netflixtechblog.com/how-netflix-scales-its-api-with-graphql-federation-part-1-ae3557c187e2)
- why graphQL: 
    - disparate teams building single-use aggregation layers 
    - teams building materialized views - data consistency issue
- why federation:
    - Bottleneck of the centralized graph API team - disconnected from the domain expertise and the product needs
- Studio API federated GraphQL example
    - new schema
        ![](/assets/images/2020-11-23-10-43-55.png)
    - architecture
        ![](/assets/images/2020-11-23-10-44-10.png)
    - Query planning and execution
        ![](/assets/images/2020-11-23-10-43-12.png)
    - detailed query plan
        ![](/assets/images/2020-11-23-10-42-25.png)
- architecture evolution
    ![](/assets/images/2020-11-23-10-44-47.png)

