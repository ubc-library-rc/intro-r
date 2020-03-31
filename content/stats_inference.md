---
layout: default
title: Inference Statistics
parent: Outline
nav_order: 5
---

## Inference Statistics


Please make sure you have merged the two datasets. Check [Merging](data_merge.md) for instructions.
{: .prereq}


### Hypothesis testing

From [Wikipedia](https://en.wikipedia.org/wiki/Statistical_significance):

To determine whether a result is statistically significant, a researcher calculates a `p-value`, which is the probability of observing an effect of the same magnitude or more extreme given that the null hypothesis is true.

The null hypothesis is rejected if the p-value is less than a predetermined level, `α`.

`α` is called the significance level, and is the probability of rejecting the null hypothesis given that it is true (a type I error). 

`α` is usually set at or below 5%.

<img src="{{site.baseurl}}/content/figures/normal_curve.png">

Our null hypotheses

**H<sub>01</sub> There is no difference in the Average temperature in the `gas & oil` and the `electronic` era**



### Independent T-test

It is often used to see whether there is a group difference in continuous data **between two groups** 

We can only run a T-test if our model follows certain assumptions:

1. Independence
1. Normality
1. Equal variance


Input
{: .label .label-green }
```R
t.test(AverageTemperature ~ era, data=carbon, var.eq=TRUE)
```


Output
{: .label .label-yellow }
```R
Two Sample t-test
    
data:  AverageTemperature by era
t = 3.7437, df = 54, p-value = 0.0004415
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
    0.1806106 0.5970976
sample estimates:
mean in group electronic  mean in group gas & oil 
                19.13249                 18.74364 
```

Interpreting the results:

* `t` value guides our analysis. Read more at this [link](https://blog.minitab.com/blog/adventures-in-statistics-2/understanding-t-tests-t-values-and-t-distributions)
* `df = 54` degrees of freedom 
* `p-value < 0.0004415` is smaller than `α = 0.05` so that means that we can reject the null hypothesis


* Which one seems higher?
    * mean in group `gas & oil` = `18.74364`
    * mean in group `eletronics` = `19.13249`

<img src="{{site.baseurl}}/content/figures/boxplot.png">    

***

<br><br>

## Correlation


**H<sub>02</sub> Is there any association between the `AverageTemperature` and the `AverageCarbonEmission`  ?**

### Pearson's correlation

Is used to examine associations between variables (represented by continuous data) by looking at the direction and strength of the associations


Input
{: .label .label-green }
```R
cor.test(carbon$AverageTemperature, carbon$AverageCarbonEmission, method="pearson")
```

Output
{: .label .label-yellow }
```R
    
Pearson's product-moment correlation

data:  carbon$AverageTemperature and carbon$AverageCarbonEmission
t = 14.919, df = 54, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
    0.8299122 0.9386169
sample estimates:
        cor 
0.8970832 
```    


Interpreting the results:

* `p-value < 2.2e-16` so that means that there is statistically significant correlation between `temperature` and `carbon emission`


* How strong is the correlation  `cor` = `0.8970832` 

* Interpretation varies by research field so results should be interpreted with caution
    
* `cor` varies from `-1` to `1` positive values indicate that an increase in the `x` variable increases the `y` variable. In this case, a value closer to `1` means a strong positive correlation

<img src="{{site.baseurl}}/content/figures/correlation.png">