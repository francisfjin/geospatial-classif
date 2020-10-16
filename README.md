# Geospatial Socioeconomic Mobility in America

Jupyter notebook here: [finalproject.ipynb](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/finalproject.ipynb)

Final report here: [final project report!](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/FinalReport.pdf)

## Topic

Project addresses the geographical variations in socioeconomic mobility amongst children in minority communities across America using Binary/Multi-label Classification machine learning methods. The model predicts the level of future socioeconomic mobility using a variety of social, educational, and economic features, and highlights the most important features contributing to successful upward mobility, while deploying interactive visualizations with Plotly to portray results. 

## Data

Source: [Opportunity Insights](https://opportunityinsights.org/data/).

[Neighborhood Characteristics by Commuting Zone](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/CZ_neighborhoodcharacteristicsbycsv.csv)

[Geography of Mobility: Commuting Zone Characteristics - Definitions and Data Sources](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/online_data_tables-8.xls)

## Data Cleaning and Pre-processing

Methods: Importing XLS and CSV files, slicing excel sheets, filtering for minority communities, cleaning and renaming columns, grouping by and merging on Commuting Zone, a unique numeric identifier for communities ranging across the entire United States. Resulting dataset has 40 features and 500 entries. 

Target variable is a metric to measure socioeconomic mobility, deemed “Absolute Upward Mobility” and engineered from the original [paper](https://opportunityinsights.org/paper/land-of-opportunity/) from Opportunity Insights. Defined as the mean future income rank of children whose parents are at the 25th percentile of the national parent income distribution. 


## EDA

Investigates statistical correlation of features vs. target variable, and displays heat maps using Seaborn Library of relationship. Also investigates distribution of target variable using Matplotlib graphs. 


## Feature Selection

Uses Sklearn library's Mutual Information Classification to create feature importance rankings. 

## Model Selection and Results

Binary Classification
- Logistic Regression with 5-fold Cross-Validation, Elastic Net Regularization, Hyper-parameter Tuning, Standard Scaler. (~90%/~85% accuracy)
- Ensemble methods: Random Forest Classifier, Gradient Boosting Classifier
- GridSearchCV hyper-parameter tuning

K-Means Clustering
- Optimal number of clusters using elbow method

Multi-Label Classification
- Logistic Regression with 10-fold Cross-Validation, Elastic Net Regularization, Hyper-parameter Tuning, Standard Scaler (~80%/75% accuracy)
- Gradient Boosting Classifier
- GridSearchCV hyper-parameter tuning

## Visualizations

Geopy Library for longitude/latitude coordinate identification for communities

Plotly Scattergeo for interactive map of USA of results

<map1.jpg>
<map2.jpg>














