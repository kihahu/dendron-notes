---
id: d4dd9201-c58d-4f4d-aa38-498c8c6e6267
title: Survival Analysis
desc: ''
updated: 1605297451413
created: 1605125570606
---
# Survival analysis
Survival analysis is a branch of **statistics** for analyzing the expected duration of time until one or more events happen, such as death in biological organisms and failure in mechanical systems. - [wiki](https://en.wikipedia.org/wiki/Survival_analysis)

Historically, originally developed and used by acturaries and medical researchers to estimate population lifetimes. 

- [Video: Censoring](https://www.youtube.com/watch?v=vX3l36ptrTU)
    ![](/assets/images/2020-11-11-15-12-53.png)
    - **Assume**: censoring is non-informative - being censored or not is not related to the probablity of event happening

- [Video: Survival Function, Hazard, & Hazard Ratio](https://www.youtube.com/watch?v=MdmWdIV5k-I)
    - **Survival function**: S(t) = P(T>t) = prob. of survival beyond time t
    - **Hazard**: HAZ = P(T< t + dt | T >t)
             = prob of dying in next few seconds, given alive now
    - **Hazard ratio** (HR)  , prob of dying in next few seconds given exposure vs. not 
    
        \\(  HR = {HAZ, x=1 \over HAZ, x=0} \\)
    
- [Video: part 3](https://www.youtube.com/watch?v=K7bmmbD7KIg)

    model | Kaplan-Meier | Exponeital | Cox-PH model
    ------|--------------|------------|-------------
    type | non-parametric | parametric | semi-parametric
    prob | Simple <br>  can est S(t) | can est S(t) and HR | hazard can fluctuate with time <br> can est HR 
    con |  No functional form <br> cannot est HR * | not always realistic <br> assume constant HAZ <br> Weibull model allows haz to proprotially ↗ or ↘	with time) | cannot est S(t)

- [Video: part 4- Kaplan-Meier model](https://www.youtube.com/watch?v=VJPPeUpyC6c)
    ![](/assets/images/2020-11-11-16-25-29.png)
    - censored data get incorporated for all the prob. calculations before they drop out 
    - a tick indicate censored data 
    - example graph from [water pipe break paper](https://www.researchgate.net/publication/338223962_Improving_Urban_Water_Security_through_Pipe-Break_Prediction_Models_Machine_Learning_or_Survival_Analysis)
        ![](/assets/images/2020-11-11-16-29-36.png)
          

