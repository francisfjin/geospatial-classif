# Geospatial Socioeconomic Mobility by Community in the US

Jupyter notebook here: [finalproject.ipynb](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/finalproject.ipynb)

Final report here: [final project report!](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/FinalReport.pdf)

## Problem

Project addresses socioeconomic mobility amongst children in minority communities across America geographically. Using Binary and Multi-label Classification machine learning methods, the model predicts the level of future socioeconomic mobility of children in a community using a variety of social, educational, and economic attributes. The project highlights the most important community factors contributing to successful upward mobility using Feature Engineering, and deploys interactive visualizations to portray the results. 

## Data

Source: [Opportunity Insights](https://opportunityinsights.org/data/).

[Neighborhood Characteristics by Commuting Zone](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/CZ_neighborhoodcharacteristicsbycsv.csv)

[Geography of Mobility: Commuting Zone Characteristics - Definitions and Data Sources](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/online_data_tables-8.xls)

## Data Cleaning and Pre-processing

First dataset CSV of neighborhood characteristics, from which we grab certain racial share data and apply a filter for just the minority communities, grouping by Commuting Zone, a unique numeric identifier for communities ranging across the entire United States. Our second dataset is an XLS file from which we import the two sheets: Online Data Table 5 and Online Data Table 8. We merge the two datasets on Commuting Zone, resulting with a dataset of 40 features and 500 entries. 

The target variable is the metric we use to measure socioeconomic mobility, deemed [“Absolute Upward Mobility”](https://opportunityinsights.org/paper/land-of-opportunity/). It is the mean rank (in the national child income distribution) of children whose parents are at the 25th percentile of the national parent income distribution. The paper goes into great comprehensive detail of this ranking method, as well as data sources used such as Census Data and IRS tax filings, and adjustments for robustness of the metric. 


## EDA

Correlation tables and heat maps for features vs. the target variable (labeled ‘am, 80-82 cohort’). 

Distribution of the target variable with visualizations, noting a relatively normal distribution. 

Target variable labels from the Absolute Upward Mobility metric for both Binary and Multi-label Classification. 


## Feature Selection

I create a function for Mutual Information Classification to create feature rankings for binary and multi-label Classification and print top features. These results are consistent with the correlation EDA from before. 


## Model Selection and Results

Best results for both Binary and Multi-Label Classification from LogisticRegression with Cross-Validation and Hyperparameter tuning with Elastic Net Regularization. 


## Visualizations

Utilizing Plotly for interactive graphical visualizations, displayed the results for both Binary and Multi-label Classification. <Link to Plotly visualizations here>. 

Hover over any city to view its Actual vs. Predicted mobility label. Note the higher accuracy of the model, the more identical the map colors will be. 














