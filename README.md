# Housing-in-Landon
This project is about the housing market of London in the years between 1995 and 2020. 

I had performed exploratory data analysis with the goal of discovering new information and answering the following questions:
1. How has the housing market (average house price and number of houses sold) changed over the years in different boroughs of London? How does it compare to England?
2. What factors affected it the most?

## Libraries

I start by importing the necessary libraries and setting some parameters for the whole notebook (e.g. the display format for the pandas library).

## Datasets

I am going to use the [Housing in London]dataset. It contains two csv files (housing_in_london_monthly_variables.csv and housing_in_london_yearly_variables.csv) with a lot of relevant information such as the monthly average house prices, yearly mean and median salary for residents of each area, etc.

The data is split by areas of London called boroughs, but some of the instances correspond to other UK regions (like North East, West Midlands, etc.).

Additionally, I am going to use a third dataset for plotting maps (London Borough and Ward Boundaries up to 2014 )

## Housing over the Years

I am going to focus on the average price and the number of houses sold in each area. 

For this task, we need two datasets:
1.	housing_in_london_monthly_variables which contains monthly information about the London boroughs and the other UK regions, and
2.	London_Borough_Excluding_MHW.shp for plotting maps.

There are 7 attributes in total. An instance represents a London borough if 'borough_flag' equals 1. The meaning of the rest of the attributes can be easily inferred from their name.

The method `info()` can give us valuable information such as the type and the number of missing values in each attribute:
Two attributes, 'houses_sold' and 'no_of_crimes', have missing values. I shall drop the whole 'no_of_crimes' attribute since almost 50% of its instances have NaN values. 

It's easier to replace missing values in the 'houses_sold' attribute as only a small portion is missing. I shall use the mean value for the same area for all years in each case. Of course, someone could argue that this number would change over the years, but I could assume that the final results won't be affected due to small number of values being changed.

## Data Exploration

According to Google, there are 33 boroughs in London (32 + the City of London). Is that the case in our dataset?
It is! How many and which regions are outside of London?

## London VS England
I can now split the dataset into two: one for boroughs in London and one for the other regions of England:

## Average Price

The `groupby()` method allows us to calculate the mean 'average price' for each 'date':
In overall, the average price follows an upward trend during the studied time frame, with London always having a higher average price. 
- This upward trend was disrupted by the Great Recession (2007-209), hence the significant decline starting from 2007. London apparently recovered quickly and the average price increased rapidly until 2016. England followed a similar behaviour but with a moderate rise in the same period.
- Arguably, the [Brexit referendum] had an impact in London housing since the average price hit a plateau after 2016. It seems the rest of England wasn't affected as much from the referendum.
The number of houses sold in London dropped sharply during the financial recession and it seems that it hasn't completely recovered since,  
- Interestingly, there is spike in March 2016 which at first sight looks like an artefact. That is not the case, because people were actually trying to avoid a new legislation that came into effect in April 2016 and imposed an increase in the tax bill on buying a second home. 
- Again, the referendum resulted in a downward trend starting from July 2016.

## Factors Affecting Housing

### Preparing the Final Dataset

## Correlation

For this question I need to import the third and final dataset (housing_in_london_yearly_variables) which I am going to merge with the monthly dataset.
It doesn't come as a surprise that apart from the year, the average price in London has a significant positive correlation with the median and mean salary along with the number of jobs in a borough. 
- There is small positive correlation with life satisfaction. More data for this attribute would be useful.
- As I discussed earlier, the most affluent boroughs happen to be small (see map) which explains the negative correlation with the size of an area. 
- The average price is also affected by the number of houses sold, since the former goes up when the later decreases (people sell higher when less houses are sold?).

# Conclusions

The main conclusions are the following:

- The average price in London boroughs is higher compared to the rest of England. It has been affected by major financial and political events (such the Recession and Brexit), but has significantly increased from 1995 to 2019 (by a factor of 5),

- Affluent regions such as Kensighton and Westiminister have the highest average price, 

- The number of houses sold plummeted after the recession, streadily increased until 2016 but then again dropped after the referendum, 

- As anyone could predict, the main factor that influences the average price is the financial prosperity of the corresponding borough. Higher salaries and more jobs result in higher prices.
