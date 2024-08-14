# London Housing Project

*By: Katia Lopes-Gilbert*

<span style="text - decoration: underline;">Project Overview</span>

I was tasked to analyze housing price data from the boroughs of Greater London to answer the following question:

**Which boroughs of London have seen the greatest increase in housing prices, on average, over the last two decades?**

To answer this question, I was provided with a dataset that captured average home prices each month in each borough from 1995 to 2023. I adhered to the four stages of the Data Science Pipeline to 1) source and load the data, 2) clean, transform and visualize the data, 3) conduct some modeling, and 4) evaluate the information I produced.

According to [Wikipedia](https://en.wikipedia.org/wiki/List_of_London_boroughs), London has 32 boroughs, not including the city of London: *City of Westminster, Kensington and Chelsea, Hammersmith and Fulham, Wandsworth, Lambeth, Southwark, Tower Hamlets, Hackney, Islington, Camden, Brent, Ealing, Hounslow, Richmond upon Thames, Kingston upon Thames, Merton, Sutton, Croydon, Bromley, Lewisham, Greenwich, Bexley, Havering, Barking and Dagenham, Redbridge, Newham, Waltham Forest, Haringey, Enfield, Barnet, Harrow, and Hillingdon.*

**Summary of Method for Analysis:**

<span style="text - decoration: underline;">Cleaning</span>: The first thing I realized after checking out the first few rows of data was that it would need to be transformed before analysis. Specifically, my end goal would be to have each variable as a column (borough name, date, and average price) and each observation as a row. We learned that this is a more machine readable format and makes analyzing large datasets easier. After going through various pre-processing steps (removing blank columns, null values, and irrelevant data like id numbers) and transposing the data, I was able to melt the DataFrame. The new cleaned DataFrame included boroughs as my identifying variables, and unpivoted the data with average home prices for each date instance. 

<span style="text - decoration: underline;">Transforming</span>: I needed to subset the data to only include details for the 32 London boroughs. I also separated the year and month into their own columns for future analysis. 

<span style="text - decoration: underline;">Analysis</span>: From here I started to calculate some summary statistics and visualize the data. I also created new columns to calculate which borough experienced the greatest increase in housing prices on average by GBP, by percent change, and using price ratios from 1995 to 2023. I also was curious to look at the variations in price month-to-month, more on that later. 

**Main Observations:**

Through my analysis I determined that the Hackney borough has experienced the greatest increase in housing prices since 1995, with a housing price ratio of 0.106. The percent change over time (not adjusted for inflation) was 842% increase since 1995. Although this borough, and the four others that followed (Southwark, Waltham Forest, Lambeth, and Lewisham) experienced the highest increase in average house price over time, they are not the most expensive boroughs in Greater London.

The top 5 most expensive London boroughs in 2023 were the following: Kensington & Chelsea, Camden, Richmond upon Thames, Hammersmith & Fulham, and Islington.

**Other Observations:**

I wanted to look at the variations in home prices from 2019 to 2023 by aggregating average home prices for each month to see if certain times of the year tend to have higher average home prices. I chose to limit the data to the top 10 boroughs with the highest coefficient of variation (CV), which calculates the standard deviation / mean. I went with the CV method versus just looking at the standard deviation because there is a significant difference in average price for various boroughs, especially when including Kensington & Chelsea. This will allow me to standardize my measure of dispersion across the boroughs regardless of their average home prices.

Most of these boroughs had overall lower home prices in the beginning of the year (Jan-Apr) compared to later in the year (May-Dec). Many of these boroughs experienced higher increases in home prices right around when summer starts (May or June). Two of the boroughs experienced decrease around the fall (Waltham Forest and Kensington & Chelsea) which is interesting. Further analysis of socio-geographical factors would be needed to see why those two boroughs increased while the others did not.

**Challenges**

I included my first iteration of my project on github as a draft to compare my initial process for cleaning. I was able to make significant improvements to reduce the lines of code after thinking through ways to optimize my cleaning process. For example, I initially included the ID column through the cleaning phase, but later realized this was irrelevant as the borough names were all unique. Also, with this step, I struggled to rename the column from NaT to ?date? because I didn?t know NaT was not a value that the .rename() works on. I was able to work through this through looking up the issue on StackOverflow, but I ended up avoiding this altogether in my final project interaction because ID was not a relevant field.

Another example was when I wanted to find the mean average price for 1995 and 2023 to compute various calculations (percent change, change in total GBP value, and price ratios), I created two separate DataFrames and merged them, which although this was not incorrect and was good practice for topics we learned, it was not the most efficient way to process this data. I was able to reduce the lines of code by first subsetting my london_boroughs dataset by my years of interest, and then created a pivot table to calculate the mean of the average price column for each year and borough. I was able to get to this solution by reviewing my course notes and think through how to simplify my steps when subsetting DataFrames.

**Future Analysis**

Something I was curious about calculating and then visualizing was the change in rank for greatest increases in price over time. I found an [article](https://towardsdatascience.com/7-visualizations-with-python-to-express-changes-in-rank-over-time-71c1f11d7e4b) that shows how this could be created using Plotly. I would want to show an interactive plot of each borough's change in rank over time. I would need to add a new column rank that would identify each borough?s rank based on price ratio for the years of interest. But first, I would need to calculate cumulative price ratios between the years from 1995 to 2023. I am not quite sure how to accomplish this yet. 

Another thing that would be interesting would be to compare demographic data for each of the boroughs. I would specifically be interested in answering the following question, ?Do the boroughs with the highest changes in price ratios show current signs of gentrification??.
