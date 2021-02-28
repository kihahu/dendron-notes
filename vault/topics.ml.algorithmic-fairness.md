---
id: c23cc850-fa67-44ac-93df-bab59ef41f46
title: Algorithmic Fairness
desc: ''
updated: 1614537039740
created: 1607537151392
---

### Algorithmic Fairness from a Non-ideal Perspective
- author/speaker: Zack Lipton  
- https://arxiv.org/abs/2001.09773 


- important moments:
    - ProPublica machine bias article from 2016 - a galvanizing event prompting interest: https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing 
    - [Gender Shades](http://proceedings.mlr.press/v81/buolamwini18a.html)- 2018. unbalanced dataset of facial benchmarks 
    - biased allocation of healthcare - https://www.theverge.com/2019/10/24/20929337/care-algorithm-study-race-bias-health 
-  Philosophy of justice 
    - https://plato.stanford.edu/entries/justice/
        - obligation ("one's due") in contrast to charity
        - resolve conflicts when interests clash
        - impartiality - two cases relvantly alike should be treated similarly 
    - convservative (conserving existing norms) vs ideal (demand reform of norms and practicies) 
    - corrective (bilateral, wrong-doer <> wronged ) vs distributive (allocating goods to individuals, mutltilateral with a distributing agent)
    - procedural (procedure) vs substantive (end result)
    - comparative (a position was offered to a less qualified candidate) vs non-comparative (regardless of comparison, e.g. basic human rights)
        - ML disccussion often focus on comparative. should also consider non-comparative
    - scope of justice 
    - ideal and non-ideal theorizing (The Imperative of Integration - Elizabeth S. Anderson)
        - ideal:
            - imagine perfectly just world  (Rawls)
            - try to minimzie discrepancy between reality and ideal
            - e.g. been used to argue against affirmative acction - ideal world is color blind 
        - non-ideal:
            - understand causual explanation of the problem, determine waht can be done and who to correct it. 
        
- economics 
    - "the economics of discrimination" - Becker 
        -  simulation of employer taste-based discrimination
    - Arrow's Rebuttal to Becker 1973 
        - imperfect information as alternative cause 
    - "Statistical theory of racism and sexism"
        - Efficient candidate screening under multiple tests and implications for fairness
 https://arxiv.org/abs/1905.11361
            - concerns noise 
            - by adjusting number of interviews. hitting boundary on left, can equalize FP and FN across groups w different noise level 
                - but more num of interviews can negatively affect candidates too 
        - Will Affirmative-Action Policies Eliminate Negative Stereotypes?
            - Stephen Coate and Glenn C. Loury
            - https://www.brown.edu/Departments/Economics/Faculty/Glenn_Loury/louryhomepage/papers/Coate%20and%20Loury%20(AER%201993).pdf
            - even when groups are equal ex ante, equilibrium outcomes following some internventions can appear to confirm negative sterotypes 

- ML fairness
    - https://www.theatlantic.com/technology/archive/2018/05/machine-learning-is-stuck-on-asking-why/560675/?utm_source=twb 
         - "ML is stuck on ... learning associations "
         - it learns associations and not causal relations 
         - on one hand, curve fitting turned out useful many places
         - but in many problems, curve fitting is not enough

    - http://approximatelycorrect.com/2016/11/07/the-foundations-of-algorithmic-bias/ 
    - taking inspiration from law: 
        - title 7 of civil rights law 
            - disparate treatment 
                - addresses **intentional** discrimination
                    - protected characterstic 
                    - also via proxy variables 
                    - with exceptions e.g. if goal is to promote diversity
                - what does intention mean in ML context? 
            - disparate treament   
                - 3 tests:
                    - plaintiff must demo statistical disparity (4/5 rule)
                    - defendent must show descirions are justified by business necessity 
                    - plaintiff must show defendent can achieve goal w alternative practice 
                - first one can be done using stats. 
                - later 2 of the 3 tests of the above are not well adressed by ML, require causal reasoning 
- typical 
    - treatment parity
        - output does not depend on sensitive characteristic
            - Model cannot use that feature 
    - impact parity 
         - outcome independent of group status
            - model can use the feature, but result algo outcome is indenpdent 
                ![](/assets/images/2020-12-10-16-11-01.png)
    - representational parity 
        - the input map to some representation that you can't infer their demographics 
        - entails impact parity
    - equalized odds / opportunity parity 
        - equal FN and/or FP rates 
- problem 
    - the different parities are mutually irreconcilable 
    - statisctical parity may not capture legal/philosophical notions 
    - lack ingredients to determine just action
        - how did disparities arive
        - impact of the decision
        - responsibilities of the decision maker 
- "impossibility" theorem: 
    - if we start from a **non-ideal world**, no set of action can simultaneously satisfy all the ideal 
    - meeting the ideal in some respect may require widening other gaps 
    - "equity" - peyton young, 1994
        - different definition of equity which all seem reasonable by itself, when together causes non-reconcible conflict 
    => must make some choices 
- problem applications of attempts for fair algorithm 
    - ![](/assets/images/2020-12-10-16-20-04.png)
        - for maximizing impact disparity, treatment disparity is optimal (theortical)
        - if other features sufficiently can encode the sensitive feature, result is indistinguishable from teatment disparity (theortical)
        - if other features partially encode sensitive feature => empirical side effects
            - recorders within group that makes no (not procedurally justifiable)
            - produces potentially bizarre incentives to conform to steortype 

        - example case study of gender study in CS admissions
            - when applied DLP, the decisions were flipped neg to pos, for candidates that based on other traits were more likely to be female and vice versa 
                - in effect hurt female candidates who were applying to fields that are more male dominated 
         
- interesting research to follow
    - causal approaches to fairness
        - counterfactual fairness (Kusner 2017)
        - causal explanation (bareinboim 2017)
        - sensitive to subjectivity (different interpretations of the cause)
        - outsource the key issue to humans 
    - feedback loops - next-step or equilibrium outcomes in a dynamic model 
        - Delayed impact of fair ML, Liu et al
        - Social Cost of strategic classification / Disparate effects of Strategic manipulation
        - Runaway Feedback Loops in predictive Policing
        
