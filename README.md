# Analyzing-Crime-in-Seattle
Welcome to the README file of our project: Analyzing crime in Seattle. This project analyzes data of reported crimes in Seattle to better understand relationships of various parameters like the Seattle neighborhood, time of day, coordinates, to crime in Seattle. This project was created by two students at the University of Washington, Yushi Nakaoka and Zachary Grybos.
This project attempts to answer the research questions below using various data analysis methods.
Research Questions:
1. What are the demographics of the city of Seattle in terms of population? Which areas do these demographics live? Which areas have more people of color or more diverse? What is the average household size and where are the most single residents? 

2. What is the average time per crime and area for the start to report? What crime has faster and slower report times? Which areas have a faster or slower start to report time?

3. What were the most common crimes in specific areas in Seattle? Which areas had the least of a certain crime, which had the most?

4. How well can coordinates and the time of incident predict the type of crime reported?

## Authors
Yushi Nakaoka
Zack Grybos

## Prerequisites
Our program requires a functioning python IDE and python itself. Interactive code environments such as a Jupyter notebook also works as well. Our installation process also requires pip. Although most users already have it, below is a link to the pip documentation on how to install and upgrade pip.

https://pip.pypa.io/en/stable/installing/

Required Libraries:

Pandas

Geopandas

Plotly

Sklearn

Shapely

Datetime

Matplotlib

Seaborn


In addition, five datasets must be downloaded. three are csv files, one is all reported crime in Seattle from 2008 to present,
Another is the population statistics of Seattle based on the 2010 census and census tracks, The final one is the household statistics of Seattle based on that same 2010 census and census tracks.
Finally the last two datasets are GeoJson files of Seattle, one is with boundaries of Micro-Community Policing Plan(MCPP) areas, while the other is the 2010 census tracks.

[SPD Crime Data: 2008-Present]https://data.seattle.gov/Public-Safety/SPD-Crime-Data-2008-Present/tazs-3rd5

[MCPP map]https://gisdata.seattle.gov/server/rest/services/SPD/SPD/MapServer/4/query?where=1%3D1&outFields=*&outSR=4326&f=json

[2010 Census Tracks]https://data.seattle.gov/dataset/Census-Tracts-2010/274q-u6zt

[2010 Census Tracks Population Statistics] https://data.seattle.gov/dataset/Census-Tract-2010-Population-Statistics/fyem-s9qe)

[2010 Census Tracks Household Statistics] https://data.seattle.gov/dataset/Census-Tract-2010-Housing-Statistics/i5a7-p735


## How to run
Our program is divided into several parts that answer the initial research questions that were created.
This how to will provide instructions for each of these python files.

q1.py : What are the demographics of the city of Seattle in terms of population? Which areas do these demographics live? Which areas have more people of color or more diverse? What is the average household size and where are the most single residents?

This python file contains five functions merge(df_census, df_house, df_pop), demographics(final_merge), plot_pop_demographics(final_merge), plot_diversity(final_merge), and plot_household_size(final_merge).

merge(df_census, df_house, df_pop):
This function merges the three datasets df1 is the geojson of the 2010 census tracks,
df2 is the housing csv dataframe based on Seattle 2010 census tracks, 
and finally df3 is the population csv that is based on Seattle 2010 census tracks.
It returns the final merged dataset that will be used in the other methods.

demographics(final_merge):
This function takes in the final merged data set and finds,
the total population of Seattle and the total population of the,
4 main racial groups Whites, Blacks, Asians and Hispanics/Latinos.
It also calculates the percentage of color or minority people in Seattle.
Finally it prints out the results.

plot_pop_demographics(final_merge):
This function takes in the final merged dataset and plots out 4 maps.
The first one is the population of Asians in Seattle,
the seconed one plots out the population of Whites in Seattle,
the third plot plots ou the population of Hispanics/Latinos in Seattle,
and finally the fourth one plots out the Black population in Seattle.
Finally it saves the visual in a png file called pop_demographics.

plot_diversity(final_merge):
This function takes in the final merged dataset and plots out two maps.
The first one shows where where people of color live in Seattle,
while the second one shows the diversity index of Seattle.
Finally it saves into a png called diversity_demographics.

plot_household_size(final_merge):
This function also takes in the final merged dataset and plots out two maps.
The first one shows the average household size by census track,
while the second one is a combine of rental occupied 1 person household,
and owner occupied 1 person household.
Finally it saves in a png called household_size.


q2.py: What is the average time per crime and area for the start to report? What crime has faster and slower report times? Which areas have a faster or slower start to report time?

This python file has ten functions, get_time_diff(df), time_diff_crime(df), max_time_diff_by_sector_area(df), min_time_diff_by_sector_area(df), time_diff_area(df), number_of_crime_per_type(df), total_number_of_crimes(df), crime_by_sector(df), max_crime_by_sector(df), min_crime_by_sector(df)
get_time_diff(df):
This function takes in the crime dataframe and compares,
the time difference between the start of the crime,
to the report time of the crime.
Finally it prints out the column 'Difference Datetime'

time_diff_crime(df):
This function takes in the crime dataframe and prints out,
the time difference between start and report times by crime.

time_diff_area(df):
This function takes in the crime dataframe and prints out,
the time difference between start and report times by area of Seattle.

max_time_diff_by_sector_area(df):
This function takes in the crime dataframe and prints out,
the max difference between start and report times by crime and sector.

min_time_diff_by_sector_area(df):
This function takes in the crime dataframe and prints out,
the min difference between start and report times by crime and sector.

number_of_crime_per_type(df):
This function takes in the crime dataframe anda prints out the number of crimes,
per type of crime in Seattle.  

total_number_of_crimes(df):
This function takes in the crime dataframe anda prints out the number of crimes,
overall in Seattle.  

crime_by_sector(df):
This function takes in the crime dataframe anda prints out the number of crimes,
per area/sector in Seattle. 

max_crime_by_sector(df):
This function takes in the crime dataframe anda prints out,
the max number of crimes number of crimes per area in Seattle.

min_crime_by_sector(df):
This function takes in the crime dataframe anda prints out,
the min number of crimes number of crimes per area in Seattle.


q3.py: What were the most common crimes in specific areas in Seattle? Which areas had the least of a certain crime, which had the most?

This python file contains two functions: mcpp_with_most_crime(crime), and plot_crime_in_area(mcpp, crime)

mcpp_with_most_crime(crime):

This method takes in a str value of a crime of the user's choice. This crime needs to be in the naming convention that is in the 'Offense Parent Group' column of the SPD crime data. The method outputs the MCPP with the most amount of reported crimes of that crime type.

plot_crime_in_area(mcpp, crime):

This method takes in str values mcpp and crime, and the naming conventions are those in the columns of 'MCPP' and 'Offense Parent Group' in the SPD crime report data.
The user inputs those two str values, and the method outputs a graph of the map of that MCPP, and dots of all the reported crimes of the type.
If the user inputs empty parameters, the method defaults to the map of all of Seattle and all reported crimes.


q4.py: How well can coordinates and the time of incident predict the type of crime reported?

This python file contains two functions: predict_offense(data, parameter_one, parameter_two, parameter_three) and plot_accuracies(accuracies, column, name)

predict_offense(data, parameter_one, parameter_two, parameter_three):

This method takes in the dataframe of the reported crimes, and three parameters. Although the question specifically asks for coordinates and datetime, the user can change parameters of their choice.
These parameters are confined to column names of the dataframe. Running this program will create a classifier decision tree machine learning model and predicts the type of crime that occured based on the three parameters chosen.
The model is created 50 times with each time the max_depth value increasing by one, starting with max_depth = 1.
This method returns a DataFrame called 'accuracies' that contains the accuracies of the classifier decision tree model at different max_depths(hyperparameter). This dataframe informs the user the optimal
'complexity' of the decision tree, by showing the different accuracies by each max_depth level.

plot_accuracies(accuracies, column, name):

This method takes in the 'accuracies' dataframe from predict_offense(), a column str, and a name str. The column and name should either be 'train accuracy' and 'Train' or 'test accuracy' and 'Test' respectively, based on which set of accuracies the user wants to plot from the 'accuracies' dataframe.



plot_accuracies(accuracies, column, name):

This method takes in the 'accuracies' DataFrame created in predict_offense() method, a column and name. The column should be 'train accuracy' or 'test_accuracy', and name should be 'Train' or 'Test' according to the previous parameter.
This method outputs the plot of the accuracy of the model as a function of max_depth levels.
