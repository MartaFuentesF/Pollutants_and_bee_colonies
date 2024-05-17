# Air Pollutants vs Bee Colony Populations: Using EPA and Survey Data to decide which pollutants to prioritize

**Problem Statement**

As environmental concerns continue to rise, there is a growing interest in understanding the impact of air quality on ecosystems. We aim to investigate the correlation between air quality (specifically the presence of key pollutant gases; CO, NO2, Ozone, PM2.5, PM10) and bee colony populations across different US states. Our goals for this project were threefold - 

1.  Investigate the trends and correlations between presence of pollutant gases and bee populations, over time for US states, through exploratory data analysis and visualisations.
2.  Use insights from statistical modelling to gain an understanding of the extent of impact that each pollutant gas has on bee colony numbers.
3.  Use insights from statistical modelling to gain an understanding of which pollutant gases should be prioritised for removal in order to maximise bee colony numbers - to be able to provide recommendations to any interest bodies.

**Methodology**

Our approach involved gathering and preprocessing data from multiple sources, including the [EPA's air quality measurements](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual) and [bee colony population records](https://data.world/finley/bee-colony-statistical-data-from-1987-2017). In our associated notebooks we perform exploratory data analysis on air quality and bee colony data, both seperately and together, to identify trends and relationships between air quality indicators and bee colony numbers accross the US. 

We feature engineered the data such that each state was an unweighted average of the data from each of its constituent counties. 
We produced multiple linear regression models using their coefficients, so that we could understand (in order of priority) which pollutants to prioritize removing to maximize bee colony numbers accross the US. We tried a number of variations of the models, engineering our features and trying lasso and ridge regressions, in order to find the optimum output as measured by the mean squared error and R2. (Make note of proving LINEM assumptions and and justifying why we chose the metrics we chose. 


**Data Dictionary**
quoted directly from: [USDA data, in data.world]('https://data.world/siyeh/us-bee-stats-by-state') and [EPA's air quality measurements](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual)

DESCRIPTION
Honey bee population data from 2012 to 2017 from the US Department of Agriculture.
SUMMARY
USDA data
Bee Colony Survey Data by State data was retrieved from the United States Department of Agriculture National Agricultural Statistics Service Quick Stats Dataset with the selection criteria shown in the file Search criteria for bee colony survey attached to this dataset.

Bee Colony Census Data by County data was retrieved from the United States Department of Agriculture National Agricultural Statistics Service Quick Stats Dataset with the selection criteria shown in the file Search criteria for bee colony census by county attached to this dataset.

Bee Colony Census Data by State data was retrieved from the United States Department of Agriculture National Agricultural Statistics Service Quick Stats Dataset with the selection criteria shown in the file Search criteria for bee colony census by state attached to this dataset.

Bee Informed data
The original Bee Colony Loss data is copyrighted and owned by the Bee Informed Partnership and is being used solely for educational purposes as permitted by the Bee Informed Partnership. The Bee Informed Partnership does not endorse this dataset and analysis. The original data can be found here.

Days Good
Number of days in the year having an AQI value 0 through 50.

Days Moderate
Number of days in the year having and AQI value 51 through 100.
 Days Unhealthy for Sensitive Groups
Number of days in the year having an AQI value 101 through 150.

Days Unhealthy
Number of days in the year having an AQI value 151 through 200.

Days Very Unhealthy
Number of days in the year having an AQI value 201 through 300.

Days Hazardous
Number of days in the year having an AQI value 301 or higher.  Note: The official AQI hazardous category range is 301-500.  Values above 500 are considered “Beyond the AQI” and are included in the # Days Hazardous in this report.

Days CO/NO2/O3/PM2.5/PM10
A daily index value is calculated for each air pollutant measured. The highest of those index values is the AQI value, and the pollutant responsible for the highest index value is the "Main Pollutant." These columns give the number of days each pollutant measured was the main pollutant. A blank column indicates a pollutant not measured in the county or CBSA.

---

**Summary and Recommendations**

Based on the model, the pollutants affecting bee colony poplutions the most (in order of impact)are 'Days PM2.5', 'Days Ozone', 'Days PM10'.