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
|`OUTAGE.START.TIME'`	              | This variable indicates the time of the day when the outage event started (as reported by the corresponding Utility in the region)|
|`OUTAGE.RESTORATION.DATE'`	     |This variable indicates the day of the year when power was restored to all the customers (as reported by the corresponding Utility in the region)|
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
Histogram 1 : Frequency of power outages over each Hour of Day

<iframe
  src="images/outage_frequency_hour_of_day.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



