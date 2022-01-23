# PyBer Analysis

## Overview of Project

### Purpose

The purpose of this analysis is to look at the disparity between ride data given different city types: urban, suburban & rural. To do this we looked at different assortments of our data using the ```.groupby()``` function from the pandas library. In our initial analysis we were focused on ride count, fare amount, and driver count, but we never considered looking at the average fare per ride or average fare per driver. Looking at our data in this way gave us additional insight to our previous observations.

## Results

![Pyber_summary_df](https://github.com/brand0j/PyBer_Analysis/blob/main/Pyber_summary_df.PNG)

Looking at this DataFrame you will notice that despite making up 62.7% of the Total Fares and 68.4% of the Total Rides, the Average Fare per Driver in urban cities is significantly lower than both suburban & rural cities. This is due to the fact that there are more total drivers than there were total rides. In fact, they make up 80.9% of Total Drivers across all city types.

![analysis_Fig5](https://github.com/brand0j/PyBer_Analysis/blob/main/analysis_Fig5.png)
![analysis_Fig6](https://github.com/brand0j/PyBer_Analysis/blob/main/analysis_Fig6.png)
![analysis_Fig7](https://github.com/brand0j/PyBer_Analysis/blob/main/analysis_Fig7.png)


We can visualize our data over time by using the following code. ```df = pyber_data_df.groupby(['date','type']).sum()[['fare']]``` & ```df_pivot = df.pivot(index ='date', columns ='type', values ='fare)``` to create a data frame with the total fare for each city type by the date. This enables us to select a timeframe that would cover ~4 months so we can make predictions with our data for the rest of the year. After setting the index to a datetime datatype and resampling it to get the sum of fares for each week, we get the following DataFrame & corresponding plot. 

![df_resample](https://github.com/brand0j/PyBer_Analysis/blob/main/df_resample.PNG)
![PyBer_fare_summary](https://github.com/brand0j/PyBer_Analysis/blob/main/PyBer_fare_summary.png)

## Summary

One thing that was not looked at during this analysis was the distance of each ride, but I could see this being a useful metric when structuring a fare/distance amount for each city type (increasing the fare/distance in cities with shorter average ride distances & decreasing the fare/distance in cities with longer average ride distances). The one discrepancy that sticks out immediately is that there is a surplus of drivers in urban cities. It might be useful to cut down the amount of drivers in these areas since it is the only city type where the average fare per ride is greater than the average fare per driver. With the distance of each ride being shorter in urban cities, there is no need to have this surplus of drivers. This can be illustrated with a box plot of the driver count by city type and observing the IQR of each.

![analysis_Fig4](https://github.com/brand0j/PyBer_Analysis/blob/main/analysis_Fig4.png)


On the opposite end of the spectrum, rural cities clearly have the highest average fare per ride and average fare per driver with the smallest ratio of total drivers to total rides. This would indicate that each ride is significantly longer compared to urban & suburban cities. Due to increased ride times there might be situations where customers are waiting for a prolonged period of time. To counteract this, I would advise increasing your amount of total drivers in rural cities.
