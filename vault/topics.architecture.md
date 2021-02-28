---
id: edcb01a7-1033-41f2-9428-9c3034fdc066
title: Architecture
desc: ''
updated: 1614537039735
created: 1607441965303
---

## Robert C. Martin - Clean Architecture and Design

recording: https://www.youtube.com/watch?v=2dKZ-dWaCiU
slides: https://t.co/QeDePKaJl6?amp=1
- some back of envelope math: the numer of programmers in the world is doubling every few years => half of the programmers in the world have < 5 yrs of experience 
- software is everywhere - before a programmer kills 10,000 ppl and the industry becomes a heavily regulated industry, should have discipline 
- **The architecture should scream its purpose** like architect's house plans 
    - "Object-Oriented Software Engineering: A Use Case Driven Approach" book - Ivar Jacobson
    - the web is detail - it's a type of I/O. e.g. in Unix I/O the application doesn't care what kind of thing it's writing to.
- From Ivar: 
    - **Entities** = application independent rules : even if there's no computer
    - **Interactors** = application specific business rules 
    
    ![](/assets/images/2020-12-08-11-01-32.png)

    - interactor can be tested without the web/delivery mech. 

- MVC 
    - MVC goes wrong and boundaries blur
        ![](/assets/images/2020-12-08-11-10-09.png)
    - Model View Presenter:
        ![](/assets/images/2020-12-08-11-09-25.png)
- Databases 
    ![](/assets/images/2020-12-08-11-12-42.png)

- Story of FitNesse - acceptance testing + wiki framework  
    - deferred the database 
    - ![](/assets/images/2020-12-08-11-17-07.png)

- On testing: 
    - anything on the edge of the system is hard to test, e.g. GUI 


Clean Architecture slides: https://www.dropbox.com/s/e60688nq18cnfz7/Clean%20Architecture.pdf?dl=0 
 