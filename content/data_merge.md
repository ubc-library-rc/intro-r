---
layout: default
title: Merging Data
parent: Outline
nav_order: 4
---


### Answer to exercise at [descriptive stats](stats_descriptive.md):


Input
{: .label .label-green }
```R
carbon <- read.csv("CarbonDioxideEmission.csv")

carbon <- na.omit(carbon)

carbon$CarbonDioxide <- as.numeric(carbon$CarbonDioxide)
carbon$year <- as.numeric(carbon$year)

head(carbon)
tail(carbon)

carbon  %>%
  group_by(year) %>%
  summarise(avg_emission = mean(CarbonDioxide))
```


## Can we merge data?

We now have 2 interesting datasets:

* `mydata` - we can obtain the average temperature of each year

* `carbon` - we can obtain the average carbon emission of each year

Each dataset contains part of the data needed to answer our research questions:

* H<sub>01</sub> the earth average temperature has not dramatically increased since the advent of electronics 

* H<sub>02</sub> the emission of carbon dioxide does not influence the earth average temperature

However, we may need to merge the two datasets to answer our research questions!

Notice that both datasets contain a column for the **year**. Let's use year to merge the data!


### merge( ): Merge two datasets using one or more columns


Input
{: .label .label-green }
```R
carbon <- group_by(carbon, year) %>% # 1
    summarise(AverageCarbonEmission = mean(CarbonDioxide)) # 2

newdata <- group_by(mydata, year, era) %>% # 3
    summarise(AverageTemperature = mean(AverageTemperature)) # 4

carbon <- merge(newdata, carbon[, c("year", "AverageCarbonEmission")], by="year") # 5
```




A detailed explanation explained line-by-line:

1. the `carbon` data will be updated with the result of the right-hand operation. The right-hand operation groups the dataset by year


2. after grouping, we apply the `summarise` to create a column named `carbon` the value of the column is the `mean` of the `CarbonDioxide` emission


3. we do a similar grouping operation creating a `newdata` data. 


4. this time, we are interested in the mean of the `AverageTemperature`


5. we now have two variables, one with the `year` and `AverageCarbonEmission` and another with year and `AverageTemperature`. Let's `merge` these two tables in a final `carbon` table. 

	* `by` indicates the key column to merge the two datasets

		* Our merging criteria is the `year`
	
	* We will copy two columns from the initial carbon table using `carbon[, c("year", "AverageCarbonEmission")]`

		*  this is the same as `select(carbon, year, AverageCarbonEmission)`


