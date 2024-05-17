# Prioritizing Pollutant Reduction to Minimize Bee Colony Loss: Analyzing EPA and Survey Data


**Introduction**

Environmental concerns have escalated in recent years, and the impact of air quality on ecosystems has become a critical area of research. This project investigates the correlation between air quality (specifically key pollutant gases: CO, NO2, Ozone, PM2.5, PM10) and bee colony populations across different US states. Bee populations are crucial for pollination and the overall health of ecosystems, making it imperative to understand the factors that influence their decline.


**Problem Statement**

As environmental concerns continue to rise, there is a growing interest in understanding the impact of air quality on ecosystems. We aim to investigate the correlation between air quality (specifically the presence of key pollutant gases: CO, NO2, Ozone, PM2.5, PM10) and bee colony populations across different US states. Our goals for this project were threefold - 

1. Investigate the trends and correlations between the presence of pollutant gases and bee populations over time for US states through exploratory data analysis and visualizations.
2.  Use insights from statistical modelling to understand the extent to which each pollutant gas impacts bee colony numbers.
3. Use insights from statistical modeling to understand which pollutant gases should be prioritized for removal to maximize bee colony numbers and to provide recommendations to any interest bodies.


**Methodology**

Some additional libraries may need to be imported: [GeoPandas]('https://geopandas.org/en/stable/index.html'), [Folium]('https://geopandas.org/en/stable/index.html')

Our approach involved gathering and preprocessing data from multiple sources, including the [EPA's air quality measurements](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual) and [bee colony population records](https://data.world/finley/bee-colony-statistical-data-from-1987-2017). In our associated notebooks, we perform exploratory data analysis on air quality and bee colony data, both separately and together, to identify trends and relationships between air quality indicators and bee colony numbers across the US. 

We feature-engineered the data such that each state was an unweighted average of the data from each of its constituent counties. 
We produced a Multiple Linear Regression Model using their coefficients so that we could understand (in order of priority) which pollutants to prioritize removing to maximize bee colony numbers across the US. We tried two different models: Multiple Linear Regression and Random Forest. Using R2 and RMSE to evaluate our models. 
Additionally, we examined the LINEM assumptions that are made when making linear regression inferential models. 
The scores for our models showed that they are not making good predictions. We discuss this further in our Summary and Conclusions. 


**Data Dictionary**
Quoted directly from: [USDA data, in data.world]('https://data.world/siyeh/us-bee-stats-by-state') and [EPA's air quality measurements](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual)

DESCRIPTION
Values for bee populations are in units of colonies, the Australian Academy of Science found a standard honeybee hive houses approximately 60,000 to 80,000 individuals. 

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
Number of days in the year having an AQI value 51 through 100.
 Days Unhealthy for Sensitive Groups
Number of days in the year having an AQI value 101 through 150.

Days Unhealthy
Number of days in the year having an AQI value 151 through 200.

Days Very Unhealthy
Number of days in the year having an AQI value 201 through 300.

Days Hazardous
Number of days in the year having an AQI value of 301 or higher.  Note: The official AQI hazardous category range is 301-500.  Values above 500 are considered “Beyond the AQI” and are included in the # Days Hazardous in this report.

Days CO/NO2/O3/PM2.5/PM10
A daily index value is calculated for each air pollutant measured. The highest of those index values is the AQI value, and the pollutant responsible for the highest index value is the "Main Pollutant." These columns give the number of days each pollutant is measured as the main pollutant. A blank column indicates a pollutant not measured in the county or CBSA.

---

**Summary and Recommendations**
Whilst the R-squared score is extremely low (our model explains only 0.17% of the changes in bee populations), we must take into account that this project only investigates Air Quality as a factor contributing towards bee populations, [disregarding other larger factors that may affect bee populations to a bigger extent](https://www.europarl.europa.eu/topics/en/article/20191129STO67758/what-s-behind-the-decline-in-bees-and-other-pollinators-infographic). This model also works off of aggregate measures for the entire US across the period of time for which we have recorded data and so we focus on making inferences from the coefficients above all else in order to address our problem statement. 

For our Random Forest Regression Model, we found the best Hyperparameters are:
* reg__max_depth': 3
* reg__min_samples_leaf': 4
* n_estimators': 100

Scores for Random Forest Regression Model: 
RMSE (testing data): 309866.742
R2 Score: 0.059

The R-squared score of 0.059 indicates that our model explains only a small portion of the variance in bee colony populations. Although this is an improvement from the previous R-squared score of 0.017, it still suggests that our model cannot make accurate predictions. This may indicate that other factors not included in the model influence bee populations or that the relationship between air pollutants and bee populations is more complex than our model can capture.

To support bee populations, environmental policies should prioritize reducing PM2.5, Ozone, and PM10 levels. Further research is necessary to improve model accuracy and explore additional factors affecting bee populations.