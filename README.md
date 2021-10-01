# UWFinTech_Module6_Challenge

## Housing Rental Analysis for San Francisco

This project is designed for the application of technology to real-estate markets, which will give a one-click service for people to buy properties and then rent them. This is done on San Francisco real-estate market.

## Technologies Used

Leveraging Jupyter Notebook
Gitbash CLI is used to pull and push the code from local repository to remote repository
Code written with the help of Jupyter Notebook.

---

## Libraries and Dependencies

import pandas as pd
import hvplot.pandas
from pathlib import Path


---
Jupyter notebook that contains analysis of the housing rental market data for San Francisco. The analysis is done with professionally styled and formatted interactive visualizations.
The python jupter notebook name is san_francisco_housing.ipynb

1.The python file consists of following calculations and inveractive plots:

2.Calculated and plotted the housing units per year.

3.Calculated and plotted the average prices per square foot.

4.Compared the average prices by neighborhood.

5.Interactive neighborhood map.

6.The data story.

### Calculate and Plot the Housing Units per Year

Numerical and visual aggregation used to calculate the number of housing units per year, and then visualized the results as a bar chart.
The steps are:

The groupby function used to group the data by year. Aggregated the results by the mean of the groups. Used the hvplot function to plot the housing_units_by_year DataFrame as a bar chart. The x-axis represented the year and the y-axis represented the housing_units.

Styled and formatted the line plot to ensure a professionally styled visualization.

Note that your resulting plot should appear similar to the following image:
![Housing Units In San Francisco 2010-2016](UWFinTech_Module6_Challenge/Images_Module6_Challenge/zoomed_by_year.png)

What’s the overall trend in housing units over the period that you’re analyzing?
As per the data and interactive plot drawn, the trend of housing units in San Fransciso over the period of 2010-2016 is increasing year by year.

### Calculate and Plot the Average Sale Prices per Square Foot

Numerical and visual aggregation used to calculate the average prices per square foot, and then visualize the results as a bar chart.

Group the data by year, and then average the results. What’s the lowest gross rent that’s reported for the years that the DataFrame includes?

A new DataFrame created and named prices_square_foot_by_year by filtering out the “housing_units” column. The new DataFrame includes the averages per year for only the sale price per square foot and the gross rent.

hvPlot to plotted the prices_square_foot_by_year DataFrame as a line plot.
Styled and formatted the line plot to ensure a professionally styled visualization.

Resulting plot image:

![Sale Price Per Square Foot and Average Gross Rent - 2010-2016 - San Francisco](UWFinTech_Module6_Challenge/Images_Module6_Challenge/Line_plot_sale_price_per_Sqr_foot_Gross_Rent.png)

Did any year experience a drop in the average sale price per square foot compared to the previous year?
Ans: Yes there is a drop in sale price per square foot in the year 2011 with value "369.344" comparing to the year 2010 with value "341.903". As per the line plot demonstration, other than that the prices never dropped till 2016. There is an increasing trend from the year 2011 to 2016.

If so, did the gross rent increase or decrease during that year?
Ans:The gross rent increased from 2010 to 2011, eventhough sale price per square foot dropped for that particular year.

### Compare the Average Sale Prices by Neighborhood

Interactive visualizations and widgets used to explore the average sale price per square foot by neighborhood. 

A new DataFrame that groups the original DataFrame by year and neighborhood. Aggregated the results by the mean of the groups.

Filter out the “housing_units” column to create a DataFrame that includes only the sale_price_sqr_foot and gross_rent averages per year.


Created an interactive line plot with hvPlot that visualizes both sale_price_sqr_foot and gross_rent. Set the x-axis parameter to the year (x="year"). Used the groupby parameter to create an interactive widget for neighborhood.

Style and format the line plot to ensure a professionally styled visualization.

```prices_by_year_by_neighborhood.hvplot(
    x='year',
    y=['sale_price_sqr_foot', 'gross_rent'],
    groupby='neighborhood',
    xlabel='Year',
    ylabel='Gross Rent/Sale Price Per Square Foot',
    title='Sale Price Per Square Foot and Average Gross Rent-2010-2016-By Neighborhood')
```

Image:

![Sale Price Per Square Foot and Average Gross Rent-2010-2016-By Neighborhood](UWFinTech_Module6_Challenge/Images_Module6_Challenge/Sale_price_per_sqr_foot_gross_rent_neighborhood.png)

For the Anza Vista neighborhood, is the average sale price per square foot for 2016 more or less than the price that’s listed for 2012?
Ans:  As per the interactive plot, the average sale price per square foot for the year 2016 is less with value 88.402 than to the year 2012 with value 344.491. 


### Build an Interactive Neighborhood Map

The geospatial relationships in the data is explored by using interactive visualizations with hvPlot and GeoViews. To build the map, the sfo_data_df DataFrame (created during the initial import) used, which includes the neighborhood location data with the average prices. 

Read the neighborhood_coordinates.csv file from the Resources folder into the notebook, and created a DataFrame named neighborhood_locations_df. The index_col of the DataFrame is set to “Neighborhood”.

The original sfo_data_df Dataframe used, created a DataFrame named all_neighborhood_info_df that groups the data by neighborhood. Aggregated the results by the mean of the group.

Reviewed the two code cells that concatenate the neighborhood_locations_df DataFrame with the all_neighborhood_info_df DataFrame. Note that the first cell uses the Pandas concat function (Links to an external site.) to create a DataFrame named all_neighborhoods_df. The second cell cleans the data and sets the “Neighborhood” column. 

Using hvPlot with GeoViews enabled, created a points plot for the all_neighborhoods_df DataFrame.

```all_neighborhoods_df.hvplot.points(
    "Lon",
    "Lat",
    tiles="OSM",
    geo=True,
    size="sale_price_sqr_foot",
    color="gross_rent",
    frame_width=700,
    frame_height=500,
    title="San Francisco Geo Plot For Neighborhood with Average Gross Rent And Sale Price Per Square Foot")
    
```

Note that your resulting plot should appear similar to the following image:
![San Francisco Geo Plot For Neighborhood with Average Gross Rent And Sale Price Per Square Foot](UWFinTech_Module6_Challenge/Images_Module6_Challenge/San_Franscisco_Geo_Plot.png)

Use the interactive map to answer the following question:

Which neighborhood has the highest gross rent, and which has the highest sale price per square foot?

Data Story
Based on the visualizations that created,

How does the trend in rental income growth compare to the trend in sales prices? Does this same trend hold true for all the neighborhoods across San Francisco?
Ans: Gross rental income has a increasing trend over the period of 2010-2016 in the neighborhood of San Francisco. However the sales per square foot has fluctuating trend over the period and different for different neighborhoods.

What insights can you share with your company about the potential one-click, buy-and-rent strategy that they're pursuing? Do neighborhoods exist that you would suggest for investment, and why?
Ans: The sale price per square foot from year 2010-2016 has increased from 369.344 to 697.644 but the gross rent has increased quite a lot from 1239 in 2010 to 4390 in 2016. So it shows a clear picture that the San Francisco market holds potential investment oppotunities. There are a lot of neighborhoods exist for buy-and-rent statergy. Good amount of business can be done by renting the houses as its growing every year.

As per the San Francisco Geo Plot For Neighborhood, Silver Avenue, Outer Mission, Topeka Avenue, Thomas Avenue, Scotia Avenue, Park North, Hayes Valley, Ingleside, Bayview these neighborhoods has high gross rent but low sale price per square foot giving an opportunity for investment. Also Encanto Avenue, Anzavista Avenue, Barcelona Avenue gives quite a good investment opportunity as rent is high and has the potential to get increase rent in the future with less sale price per square foot.

## Contributors

This project is designed by Swati Subhadarshini 
Emaid id: sereneswati@gmail.com
LinkedIn link: https://www.linkedin.com/in/swati-subhadarshini-89a8a538?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BhUCLlUYCSc2jK4x4khPVUQ%3D%3D

---