---
id: e9abdfa6-2451-442e-a681-5165daba5f36
title: Ch8 - Problems with distributed systems
desc: ''
updated: 1604976950965
created: 1604679379882
---

- Supercomputing
    - deals with partial failure by letting it escalate into total failure
- Cloud computing
    - Unreliable network 
        - telephone network is sync. call establish a _circuit_,  fixed, guaranteed amount of bandwidth is allocated for the call, along the entire route between the two callers. - has **bounded delay**
        - Ethernet and IP are packet-switched protocols, which suffer from **queueing** and thus **unbounded delays** in the network. These protocols do not have the concept of a circuit <- because **optimized for bursty traffic**. audio or video call needs to transfer a fairly constant number of bps. TCP **dynamically adapts the rate of data transfer to the available network capacity**. 
        - **dynamic resource allocation**: has downside of queueing, but pro: it maximizes utilization of the wire. 
        - static resource partitioning: Latency guarantees. but reduced utilization. 
    - Unreliable Clocks
        - possible to achieve good accuracy invest significant resources. e.g. the MiFID II draft EU regulation for financial institutions requires all HFT funds to synchronize to within 100 microseconds of UTC - uses GPS receivers, the Precision Time Protocol (PTP) careful deployment and monitoring
        - typical NTP is fickle  - limited by the network round-trip time, in addition to quartz drift, etc.
        - Clock readings have a confidence interval
            - mostly not exposed, but Google’s TrueTime API in Spanner: when you ask it for the current time, you get back two values: [earliest, latest],
        - Synchronized clocks for global snapshots 
            - typically require monotonically increasing transaction ID 
            - when distributed, Spanner approach: use the TrueTime API, if A\[earliest] < A\[latest] < B\[earliest] < B\[latest], then A is before B 
            - deliberately waits for the length of the confidence interval before committing a read-write transaction 
            - to keep uncertainty small, use GPS receiver or atomic clock in each datacenter
        - problem with leader lease: 
            ```
            get request
            check lease expiration
            if not expired, handle request
            ```
            - if rely on time-of-day expiry time, then out of sync 
            - what happens if process pause between check lease and handling of request? potential causes
                - GC pause
                - virtual machine suspended due to live migrations
                - I/O blocking
                -  context-switches 