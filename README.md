# PyBer_Analysis

#### An Analysis of Ride Sharing Data by City Type

## Introduction

The purpose of this project was to analyze time-series ride sharing data (fare amount, number of rides, and number of drivers) categorized by city type (rural, suburban, and urban) for a ride sharing firm. Firstly, a dataframe was created to summarize the data by city type. The data was then organized into weekly datapoints to demonstrate changes in total weekly fare amount over a four month period (January - April 2019), with graphed results used to recommend business decisions based on city type.

## Results

### Summary Data

A summary dataframe was created created by calculating the following aggregate variables: total number of rides, total number of drivers, total fare amount, and average fare amount per ride and per drriver. The following is the code used to create data series for the required variables:

    rides_series = pyber_data_df.groupby(["type"]).count()["ride_id"]
    drivers_series = city_data_df.groupby(["type"]).sum()["driver_count"]
    total_fares_series=pyber_data_df.groupby(["type"]).sum()["fare"]
    avg_fare_per_ride = total_fares_series/rides_series
    avg_fare_per_driver = total_fares_series/drivers_series

A dataframe was created by organizing the above series into columns. The resulting summary dataframe is as follows:

![image](https://user-images.githubusercontent.com/79061124/118707936-1dca6b00-b7e9-11eb-9e0b-9959ae2cdbe1.png)

Urban cities have the highes number of drivers and rides, and rural cities have the lowest. The dataframe indicates increasing total fare amount based on number of drivers and rides, going from rural (lowest), to urban (highest). The average fare per rider and per driver show an inverse relationship with the number of rides and drivers, with rural cities having the highest average per ride and per driver fares.

### Total fare by City Type

Total weekly fare by city type for Jan - April 2019 was determined in the second part of this project. First, a dataframe was created by summing all fare by city type and date, so that each city type had a total fare amount for each date. The data was cleaned (removing index, setting date/time datatype to datetime), and weekly data for Jan - April was then extracted to create a new dataframe:

![image](https://user-images.githubusercontent.com/79061124/118709893-90d4e100-b7eb-11eb-9a4c-52f5698d832d.png)

The dataframe was then graphed as follows:

![image](https://user-images.githubusercontent.com/79061124/118710160-ec9f6a00-b7eb-11eb-9a6f-b69f4e404812.png)

As exptected, the data indicates relatively stable total fare amount over Jan - April, with the highest total fare in urban cities, and the lowest in rural cities.

## Summary/Business Recommendations

In summary, the data indicates that rural cities are underserved with the lowest number of drivers and rides, and the highest average fare amounts per driver and ride. The following practices are recommended as business decisions to alleviate this issue:

- Incentivize riders with reduced fare per ride per distance travelled. This will result in increased number of rides, which correlates positively with increased total fare.
- Incentive drivers by offering increased fare margins per ride (portion of total fare collected by driver). This will result in increased number of drivers, which correlates positively with increased total fare.
- Incentivize drivers by offering bonuses for carrying out rides in rural cities

