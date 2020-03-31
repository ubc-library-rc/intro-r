---
layout: default
title: Descriptive Statistics
parent: Outline
nav_order: 3
---

## Descriptive Statistics


### Descriptive stat with basic summary function


Input
{: .label .label-green }
```R
summary(mydata)
```


***

## Descriptive statistics with visualization 

### Creating histogram for “year” 


Input
{: .label .label-green }
```R
hist(mydata$year)
```


<img src="{{site.baseurl}}/content/figures/histogram.png">


### Creating a histogram using gpplot 2

Input
{: .label .label-green }
```R
g <- ggplot(mydata, aes(x=year))
g <- g + geom_histogram(binwidth=.9) + scale_y_continuous(trans='log2')
g <- g + theme_light()
g <- g + labs(x="years", y="Frequency", face="bold")
g
```

* `ggplot(mydata, aes(x=year))` creates a plot using `mydata` aes defines the `x`, `y` and many other axis
* `geom_histogram` defines de plot as a histogram, `binwidth` defines de width of the bars
* `scale_y_continuous(trans='log2')` transforms the scale of the graph to `log2` delete `+ scale_y_continuous(trans='log2')` and check what happens
* `theme_light()` changes the theme. There are various themes like black and white or color blind. 
* `labs(x="years", y="Frequency", face="bold")` changes the `x` and `y` labels in the plot


***

#### Create barplot for “era” 


Input
{: .label .label-green }
```R
barplot(table(mydata$era))
```


<img src="{{site.baseurl}}/content/figures/bar.png">


***

### More visualization functions with “ggplot2”

Try to run this command:


Input
{: .label .label-green }
```R
ggplot(data=mydata, aes(x=year, y=AverageTemperature)) + geom_line()
```

Can we do better?
{: .warn}

What if we can manipulate the data so that we get the `average temperature` of each `year`?


### group_by( ): Aggregates data based on the values from one or more columns



Input
{: .label .label-green }
```R
grouped_data <- mydata  %>%
    group_by(year) %>%
    summarise(avg_temp = mean(AverageTemperature))
```


Input
{: .label .label-green }
```R
head(grouped_data)
```

### Plotting the grouped data


Input
{: .label .label-green }
```R
ggplot(data=grouped_data, aes(x=year, y=avg_temp)) +
  geom_line()
```


<img src="{{site.baseurl}}/content/figures/line.png">



If we are on track, try to:
{: .warn}

### 1. load carbon dioxide data

### 2. remove NA

### 3. Change the column "CarbonDioxide" to numeric

### 4. Change the column "year" to numeric

### 5. view the data using the head( ) and tail( ) commands

### 6. get the mean CarbonDioxide emission of each year 

Don't spoil the fun. The stick figure is watching you



<img src="{{site.baseurl}}/content/figures/watch.png" width="30%">

