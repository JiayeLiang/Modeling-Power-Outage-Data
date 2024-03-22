<meta http-equiv='cache-control' content='no-cache'> 
<meta http-equiv='expires' content='0'> 
<meta http-equiv='pragma' content='no-cache'>
# Modeling-Power-Outage-Over-The-Years
**Authors**: Jiaye Liang

## Introduction
As society continues to progress electricity becomes more and more of a essential part of life. My project aims to explore how power outages severity and frequency change over time. The importance of my project is to model
the trends of power outages to give a status on the health of the power grid as our population alogn with electircity demand continues to grow. 

# Data Set Introduction
# outage, time of day of occurence
|Column	                 |Description|
|------------------------|-----------|
|`'YEAR'	`              | Indicates the year when the outage event occurrede|
|`'MONTH'`	                 | Indicates the month when the outage event occurred|
|`'U.S._STATE'`	         | Represents all the states in the continental U.S.|
|`'CLIMATE.REGION'`	              | U.S. Climate regions as specified by National Centers for Environmental Information (nine climatically consistent regions in continental U.S.A.)|
|`'CLIMATE.CATEGORY'`	          | This represents the climate episodes corresponding to the years. The cate- gories—“Warm”, “Cold” or “Normal” episodes of the climate are based on a threshold of + or - 0.5 °C for the Oceanic Niño Index (ONI)|
|`'OUTAGE.START.DATE'`	              | This variable indicates the day of the year when the outage event started (as reported by the corresponding Utility in the region)|
|`'OUTAGE.START.TIME'`	              | This variable indicates the time of the day when the outage event started (as reported by the corresponding Utility in the region)|
|`'OUTAGE.RESTORATION.DATE'`	     |This variable indicates the day of the year when power was restored to all the customers (as reported by the corresponding Utility in the region)|
|`'OUTAGE.RESTORATION.TIME'`	     | This variable indicates the time of the day when power was restored to all the customers (as reported by the corresponding Utility in the region)|
|`'CAUSE.CATEGORY'`	     | Categories of all the events causing the major power outages|
|`'CAUSE.CATEGORY.DETAIL'`	     | Detailed description of the event categories causing the major power outages|
|`'CUSTOMERS.AFFECTED'`	     | Number of customers affected by the power outage event|
|`'POPULATION'`	     | Population in the U.S. state in a year|
|`'POPPCT_URBAN'`	     | Percentage of the total population of the U.S. state represented by the urban population (in %)|

The dataset contains 1534 rows, each row refering to a major power outage. The columns listed above do not
encompass all the columns from the original data set. I have chosen to list the columns that were revelant in
my data exploration and analysis. 

---
## Data Cleaning and Exploratory Data Analysis
### Univariate Analysis Data Cleaning
I began by transforming the imported dataframe into a more readable format by giving the unamed columns their proper names and remvoing empty columns and rows at the beginning of the dataframe. The columns format was suitable so there were not typing change that were necessary. 

Below is the dataframe afer cleaning and extraction the revelant columns:

|  OBS   | year	| month |	u.s._state |     climate.region	|...| cause.category.detail	|customers.affected	| population | poppct_urban |
|-------:|:---- |:------|:-----------|:-------------------|:--|:----------------------|:------------------|:-----------|-------------:|
|  1     | 2011 | 7     |  Minnesota | East North Central |...|         NaN           |     70000         |    5348119 |   73.27      |
|  2     | 2014 | 5     |  Minnesota | East North Central |...|         vandalism	    |     NaN           |    5457125 |   73.27      |
|  3     | 2010 | 10    |  Minnesota | East North Central |...|          heavy wind   |     70000         |    5310903 |   73.27      | 
|  4     | 2012 | 6     |  Minnesota | East North Central |...|       thunderstorm	  |     682000        |    5380443 |   73.27      |
|  5     | 2015 | 7     |  Minnesota | East North Central |...|              NaN      |     250000        |    5489594 |   73.27      |

### Univariate Analysis
#### Frequency of power outages over each Hour of Day

<iframe
  src="images/outage_frequency_hour_of_day.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The histogram shows roughly normal distribution with a surprising peak where power outages most commonly occur at 3:00pm. This does make sense as power usage is highest at noon therefore most likely to cause a grid overload where electric demand exceeds supply.

#### Distribution of Customers Affected

<iframe
  src="images/customer_affected.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The histograms shows a right skewed distribution where most of major power outages affect around 100-500 thousand people and shows large power outages affecting millions residents are pretty rare.

### Bivariate Analysis
#### Population vs Customers Affected

<iframe
  src="images/pop_vs_customers_affected.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Suprisingly the scatter plot is a patternless cloud showing little to nocorrelation between population and customers affected. The scatter plot also revevals
population gaps where we create 3 groups. The groups seem to share a distribution for severity of power outages, have many small outages that affect
small numbers of people and ocassionaly having severe outages affecting many people. 

#### Customer Affected vs Outage Duration

<iframe
  src="images/outage_duration_vs_customers_affected.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The scatter plot seems like a patternless cloud with many of its points concentrated at the bottom where duration of outages are short. There are outliers on
both extremes with outages affecting many people but haveing short duration and outages affect small number of people but having long duration.

### Interesting Aggregates
#### Models the frequency of power outages across each region of United States from year 2000 to 2016

For aggregation I groupby Year and Climate Region and performed a count. The trends of the data is most prevelant when
visualized.

|  Year    | Climate.Region	| Count |
|---------:|:--------------|-------:|
|  2000    |  Central      |  4     | 
|  2000    |  North East   |  2     | 
|  2000    |  South        |  3     |
|  2000    |  Southeast    |  6     | 
|  2000    |  Southwest    |  3     | 

### Figure 1
<iframe
  src="images/year_vs_power_outage1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Figure 2
<iframe
  src="images/year_vs_power_outage2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Figure 3
<iframe
  src="images/year_vs_power_outage3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The trends of power outages across regions can seem like an uncorrelated mess shown in figures 2 and 3 or they can be
similar looking trends have same unticks and down ticks of outages shown in figure 1. Interestingly a region minimal
power outages is West North Central of United States while Northeast saw the greatest spike in number of power outages.

---
## Assessment of Missingness
### NMAR Analysis

A column that is seems to be NMAR is the months which refers to the month the power outage occured. Refering to 
other columns such as outage.start.date or outage.start.time, these columns could suggest months is MAR, they seem to be depdent
on months because they are missing as well. Thus months is most likely missing because the people who collected the data were unable 
to pinpoint an exact month to all the power outage occurences. 

Additional data that could make months MAR would be would be inclusion of documents reports with a dates regarding power outages.

### Missingness Dependency

Since I'm interested in study the severity of power outages over the years I wanted to test if dependcy existed between population and number of people affected to gauge if more heavily populated states have implement systems that would prevent widespread power outages. Therefore would see less people
being affected despite their larger population

#### Modeling dependecy of number of people affected by power outage and population
Null : The distribution of state population where data for customers affected is present is the same as the distribution for state
populaton where data for customers affected is not present

Alternative: Population distribution is different for the groups where data for customers affected is present and not present

Test statistic calcualte the absolute difference in means population

#### Dependency of number of people affected and population (Number of People Affected Not Missing)
<iframe
  src="images/pop_vs_outage_count.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Dependency of number of people affected and population (Number of People Affected Missing)
<iframe
  src="images/pop_vs_outage_count2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Using a standard p-value cutoff of 0.05 my observed statistic is not significant my calcualte p-value of 
0.3119 > 0.5 thus we dont reject the null and assume there is no depdency between population and number of customers affected.

#### Modeling dependecy of start date time and year

Null Hypothesis: The distribution for year where start date time is missing is the same as the distribution for year where start date time is not missing

Alternative: The distribution for year where start date time is missing different from the distribution for year where start date time is not missing

Test Statistic: Absolute difference in means for years

#### Dependency of start date time and population (Start Date Time Not Missing)
<iframe
  src="images/year_vs_outage_count.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Dependency of start date time  and population (Start Date Time Missing)
<iframe
  src="images/year_vs_outage_count2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Using a p-value cutoff of 0.05, my calcuated p-value of 0 < 0.05 means that I should reject the null and accept the alternative where date time of a power outage may have dependency with the year column. 

---
## Hypothsis Testing
### Question: How do major power outages differ in characteristics between densely populated states and sparesly populated state for outage duration

Null Hypothesis: Large and small states share the same outage duration

Alternative: Large have longer outage duration than smaller states

Test statistic: absolute difference in means of outage duration

I chose a p-value of significance to be 0.05 and I chose to perform a one sided test, because I believe larger states will expereince longer periods of outages. The reason is larger the state population require more expansive and complex power grids to supply everyonewith electrcity thus when issues arise they become more difficult to fix when compared to smaller power grids in small states.

The reason I chose difference in means as my test statistic is because outage duration is numerical data and taking the meansis a good aggreation strategy to compare small and large states

To clean up the data for testing I removed all the rows with NaN values and added a extra column size_category to categorize a state as small or large

<iframe
  src="images/hypothesis_test.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Using a 0.05 cutoff, my calcuated p-value of 0.0005 < 0.05 thus I should reject the null in favor of the alternative stating larger states may experience longer duration of outages that smaller states. This conclusion
might be explained by the more expansive and complex power grid required to supply electricity to a larger population. Thus when issues occurs it may be difficult to identify or locate leading to longer duration of outages.

---
## Framing a Prediction Problem

For my model I wanted to build a regression model that could predict how many people were affected by a 
power outage, because I'm interested in predicting the severity of power outages and number of people affected
is a factor for power outage severity. To score my model I will use RMSE and R^2. 


---
## Baseline Model

Qualitative: outage.duration, popden_urban
Nominal: cause.category, climate.category, u.s._state, cause.category.detail, 
### Features utlized: cause.category, outage.duration, climate.category, u.s._state, cause.category.detail, popden_urban

I chose the columns cause category, cause duration, climate.category, cause.category.detail, because I believed they would be a good indicator on the power outage serverity thus would help in predicint number of people affected. I chose cause category, climate.category, cause.category.detail for similar reasons if the cause was
vandalism then the outage would likely note be severe and would affect minimal number of people. On the other hand if the cause was a major hurricane or storm they we can expect a larger outage that affects more people.
Cause duration could also be a measure of severity where longer power outage duration duration could suggest damages maybe severe and require greater reparation time. 

I used states to highlight the different power grid infastrucutres of different states.Some state power grids are more interconnected than other more rural statesthus would see less people affected when a power station 
shuts down.State poulation density was used because I believe more densily populated people are more pacted together so a power grid in a highly populated neighborhood would affect more people than less populated neighborhood.

### Encodings
I onehot encoded all the nomial columns

### Performance
Viewing the results of my model the features I have chosen do show correlation with number of people affected with an R^2 of 0.5537662949526712, but the ability to actually predict number of people affected is poor displayed by the high RMSE value of 253310.91

---
### Final Model

#### Description
In my new model the two columns I chose to add were population and outage start time. The reason I added population and applied a standard scaling was because states with larger population means a power outage could affect more people and standard scaling was applied to population reduces the impact of large population varation across states.

I chose outage start time as my second column to add because I believe outages that occur late at night or close to dawn would affect less people, because people would typically be sleeping and wouldn't notice the power grid shutoff. A quantile scaling was chosen to cut the day into 4 parts dawn, mornging, afternoon and night
The hyperparameters I utilized was n_quantiles for outage state time which I picked by trial and erorr.

#### Performance
For the final model I chosen linear regression to predict number ofpeople affected by power outage. Looking at the  R^2 score of 0.5547042598601943 and RMSE of 252886.88037342188 which show my final model had negligible improvement.

---
### Fairness Analysis

#### Description
For my fairness analysis I chose to compare my model predictions for small states and large states. Similar to categorization I did before, I found the median of state population and set and states with a population greater than median as large and any states with smaller population as small. 

Null: My model is fair and have similar RMSE for small and large states

Alternative: My model is unfair and have different RMSE for small and large states

Test statistic: abs difference in RMSE

I will use a 0.05 p-value cutoff to determine if I choose the null or alternative

#### Analysis
When solving for the observed data my model has a lower RMSE for smaller states than larger states which had a difference of 198766.5434220316 RMSE. From the results of the permutation test, my calcualated p-value for of 0.006 is less than 0.05 so I reject the null and assume my model may not be fair when predicting number of people affected for small and large states. 
