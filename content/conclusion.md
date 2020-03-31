---
layout: default
title: Wrap-up
parent: Outline
nav_order: 7
---


### Answer to exercise at [non-parametric stats](stats_non_parametric.md):


**Mann-Whitney test**


Input
{: .label .label-green }
```R
wilcox.test(AverageTemperature ~ era, data=carbon)
```


Output
{: .label .label-yellow }
```R    
Wilcoxon rank sum test

data:  AverageTemperature by era
W = 437, p-value = 0.0002986
alternative hypothesis: true location shift is not equal to 0
```
    


***

**Spearman Correlation**


Input
{: .label .label-green }
```R
cor.test(carbon$AverageTemperature, carbon$AverageCarbonEmission, method="spearman")
```


Output
{: .label .label-yellow }
```R    
Spearman's rank correlation rho

data:  carbon$AverageTemperature and carbon$AverageCarbonEmission
S = 4452, p-value < 2.2e-16
alternative hypothesis: true rho is not equal to 0
sample estimates:
        rho 
0.8478469 
```    

***




## Conclusions from our analysis

<img src="{{site.baseurl}}/content/figures/this_is_fine.png">



## Consultations

Research Commons has a team of GAAs happy to help you analyze your data. Book a consultation online.

<img src="{{site.baseurl}}/content/figures/consultation.png">


## Feedback

<p align="center">Please, provide us <a href="http://bit.ly/RCfeedbackwinter2018" target="_blank">Feedback</a></p>