# Geospatial Socioeconomic Mobility in America

Jupyter notebook here: [finalproject.ipynb](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/finalproject.ipynb)

Final report here: [final project report!](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/FinalReport.pdf)

## Topic

Project addresses the geographical variations in socioeconomic mobility amongst children in minority communities across America. Using Binary and Multi-label Classification machine learning methods, the model predicts the level of future socioeconomic mobility in a community using a variety of social, educational, and economic attributes. The project highlights the most important factors contributing to successful upward mobility using Feature Engineering, and deploys interactive visualizations with Plotly to portray the results. 

## Data

Source: [Opportunity Insights](https://opportunityinsights.org/data/).

[Neighborhood Characteristics by Commuting Zone](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/CZ_neighborhoodcharacteristicsbycsv.csv)

[Geography of Mobility: Commuting Zone Characteristics - Definitions and Data Sources](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/online_data_tables-8.xls)

## Data Cleaning and Pre-processing

Methods: Importing XLS and CSV files, slicing excel sheets, filtering for minority communities, cleaning and renaming columns, grouping by and merging on Commuting Zone, a unique numeric identifier for communities ranging across the entire United States. Resulting dataset has 40 features and 500 entries. 

Target variable is a metric to measure socioeconomic mobility, deemed “Absolute Upward Mobility” and engineered from the original [paper](https://opportunityinsights.org/paper/land-of-opportunity/) from Opportunity Insights. Defined as the mean future income rank of children whose parents are at the 25th percentile of the national parent income distribution. 


## EDA

Correlation Tables

Seaborn library Heat Maps 

Matplotlib library Distribution and Cumulative Plots



## Feature Selection

Function using Mutual Information Classification from Sklearn library to create feature rankings for binary and multi-label Classification. 

<feature rankings.jpg>
<top ten features.jpg>


## Model Selection and Results

Binary Classification
- Logistic Regression with 5-fold Cross-Validation, Elastic Net Regularization, Hyper-parameter Tuning, Standard Scaler
- Ensemble methods: Random Forest Classifier, Gradient Boosting Classifier
- GridSearchCV 

K-Means Clustering

Multi-Label Classification
- Logistic Regression with 10-fold Cross-Validation, Elastic Net Regularization, Hyper-parameter Tuning, Standard Scaler
- Gradient Boosting Classifier
- GridSearchCV 

## Visualizations

Geopy Library for longitude/latitude coordinate identification

Plotly Scattergeo for interactive map of USA for results 

<map1.jpg>
<map2.jpg>














