# Matplotlib RideShare

## Goal
Use the Pandas Library to analyze rideshare data and visualize findings using the Matplotlib Library. 

## Process
Data was stored in two separate csv files, so the files were read into a notebook and merged  on `city` using an inner join with `pd.merge()` and stored in a data frame, `combined_data`.

#### Bubble Plot
![bubbleplot]( https://github.com/lorijta92/matplotlib-rideshare/blob/master/Images/bubbleplot-rideshare.png?raw=true)

I wanted to showcase the relationship between four variables:
* Average Fare ($) Per City 
* Total Number of Rides Per City 
* Total Number of Drivers Per City 
* City Type (Urban, Suburban, Rural)

and believed a bubble plot would showcase this best, with the total number of rides as the x-axis, average fare cost as the y-axis, city types noted by marker color, and the total number of drivers being represented by the marker size. 

I found three different city types using `.unique()` on the `type` column of the combined data. I then grouped the combined data on both `type` and `city`, storing that object in a variable named `grouped_data`.

For the total number of rides per city, I used `.count()` on the `ride_id` of `grouped_data` and further filtered those values by city type. I repeated the same process for both average fare and driver count, but used `.mean()` instead on the `fare` and `driver_count` columns. Because the driver count for each unique city was the same for every entry, `.mean()` was used so that the values could be accessed without be changed. 

All these values were then plotted in a scatter plot and formatted for color and labeling. 

Next, I wanted to find the percent of total fares, rides, and drivers by city type, which would be best depicted in pie charts. 

#### Total Fares by City Type
![totalfares]( https://github.com/lorijta92/matplotlib-rideshare/blob/master/Images/piechart-pcttotalfare.png?raw=true)

Total fares were calculated using `.sum()` on the `fare` column of `grouped_data`, first created for the bubble plot, and then separated by the three city types. The sum for each city type was stored in a variable and those variables were then plotted in pie chart.

#### Total Rides by City Type
![totalrides]( https://github.com/lorijta92/matplotlib-rideshare/blob/master/Images/piechart-pcttotalrides.png?raw=true)

Total rides were calculated using `.value_counts()` on the `type` column of the original `combined_data` data frame. No further manipulation was required, so the values were stored in an array to be plotted, with each city type being accessed through indexing. 

#### Total Drivers by City Type
~![totaldrivers](https://github.com/lorijta92/matplotlib-rideshare/blob/master/Images/piechart-pcttotaldrivers.png?raw=true)

The count of total drivers by city type has already been accessed in the bubble plot section and stored in a variable, so I used that same variable and took the sum of each city type to plot.

