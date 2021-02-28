---
id: 6011ad5f-c0b5-43f3-a3a0-cd6a09611c28
title: ML and technical debt
desc: ''
updated: 1604978257759
created: 1604977893595
---

## Machine Learning: The High Interest Credit Card of Technical Debt

* link to paper: https://research.google/pubs/pub43146/

* Complex Models Erode Boundaries
    - Entanglement
        - Generally not possible to make isolated changes - Changing Anything Changes Everything 
        - Applies to features, signals, parameter settings, etc
        - Somewhat innate to ML 
    - Hidden feedback loop 
        - ML system’s predictions end up influencing its own training data
        - May happen in surprising ways, such as two systems are dependencies of each other 
        - Can result in gradual changes not immediately visible, hard to detect and debug 
    - Undeclared consumers 
        - Changes to model impact undeclared downstream app 
        - Also potential to create hidden feedback loops 
* Dependency debt
    - Data dependency cost more than code dependencies 
        - Data dependency is harder to track than code dependencies 
        - Unstable dependency
        - Legacy features
        - Bundle features
        - episilon Features – small improvement in accuracy with huge complexity overhead
        - Correction cascade – tendency to use another model and learn a calibration layer
    
* System level spaghetti
    - Glue code - most of the code is not the model itself. 
    - Pipeline jungles
    - Dead Experimental Codepaths 
    - Configuration Debt 

