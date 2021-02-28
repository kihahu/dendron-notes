---
id: 7ec6a7fa-7000-45e0-bec0-e3aa2e3493c5
title: Async job scheduling
desc: ''
updated: 1605474086313
created: 1605473152874
---

### [Blog] Asynchronous computing @Facebook
- https://engineering.fb.com/2020/08/17/production-engineering/async/
- Problem with simple priority queues: 
    - large use cases dominate
    - bad jobs stuck 
    - uneven utilization between peaks & valleys 
- Building to scale
    - introduce **delay tolerance**
    - Capacity optimization: 
        - classifying use cases:
            - daily traffic: predictable
            - major events: semi-predictable
            - Incident response: short and spikey, unpredictable
        - Time shifting: 
            - Predictive - which data may need, precomputes and cache
            - Deferred compute
            ![](/assets/images/2020-11-15-15-53-52.png)
        - batching: 
            - reduce # of requests to other components 
            - potential high cache reuse and code warmup
    -  Capacity policy: quota and rate limiting
        - CPU instruction utilization and memory limit - when exceeded, throttle and send alert
        - rate limit on intake
    