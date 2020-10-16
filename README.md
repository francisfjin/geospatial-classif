# Geospatial Socioeconomic Mobility by Community in the US

Jupyter notebook here: [finalproject.ipynb](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/finalproject.ipynb)

Final report here: [final project report!](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/FinalReport.pdf)

## Problem

Project addresses socioeconomic mobility amongst children in minority communities across America geographically. Using Classification machine learning methods, the models predict the future level of socioeconomic mobility of children based on a variety of community-level attributes. Also, the project highlights the most important factors contributing to successful upward mobility of children using Feature Engineering techniques. 

## Data

Data is from [Opportunity Insights](https://opportunityinsights.org/data/).

Datasets: 

[Neighborhood Characteristics by Commuting Zone](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/CZ_neighborhoodcharacteristicsbycsv.csv)

[Geography of Mobility: Commuting Zone Characteristics - Definitions and Data Sources](https://github.com/francisfjin/Geospatial_SocioeconomicMobility/blob/main/online_data_tables-8.xls)

## Data Cleaning and Pre-processing

First dataset CSV of neighborhood characteristics, from which we grab certain racial share data and apply a filter for just the minority communities, grouping by Commuting Zone, a unique numeric identifier for communities ranging across the entire United States. Our second dataset is an XLS file from which we import the two sheets: Online Data Table 5 and Online Data Table 8. We merge the two datasets on Commuting Zone, resulting with a dataset of 40 features and 500 entries. 

Target Variable 

The target variable is the metric we use to measure socioeconomic mobility, deemed [“Absolute Upward Mobility”](https://opportunityinsights.org/paper/land-of-opportunity/). It is the mean rank (in the national child income distribution) of children whose parents are at the 25th percentile of the national parent income distribution. The paper goes into great comprehensive detail of this ranking method, as well as data sources used such as Census Data and IRS tax filings, and adjustments for robustness of the metric. 


## EDA

Correlation tables and heat maps for features vs. the target variable (labeled ‘am, 80-82 cohort’). 

We also investigate the distribution of the target variable with visualizations, noting a relatively normal distribution. 

We create target variable labels from the Absolute Upward Mobility metric for both Binary and Multi-label Classification. 


## Feature Selection

I create a function for Mutual Information Classification to create feature rankings for binary and multi-label Classification and print top features. These results are consistent with the correlation EDA from before. 


## Model Selection and Results

Binary Classification

Started with a simple LogisticRegression model which showed poor performance. Ensemble methods RandomForestClassifier and GradientBoostingClassifier showed extremely high scores on training data (~95%) but much lower on test data (~80%), signaling overfitting. These models are likely suffering from over-cardinality and multi-collinearity, for example the features ‘fraction of adults married’ and ‘fraction of children with single mothers’ are naturally closely related. Also, given the modest size of the dataset, complicated models are prone to over-fitting. 


Here is an example of the Feature Importances from the GradientBoostingClassifier. The highest one is again fraction of children with single mothers, but other important features not identified before include manufacturing employment share, fraction religious, growth in Chinese imports. Interesting insight.










Given the need for regularization, I scaled the data and employed LogisticRegressionCV with elastic-net regularization, 5-fold cross-validation, and hyper-parameter tuning ranges of Cs = np.logspace(-10,10,50) and L1 ratios = np.arange(0,1,.05). 

Training and test set scores both drastically improved to ~90%, with roc_auc_score consistently above 90% as well. 





K-Means Clustering

Although not originally a clustering problem, I investigated the data with the K-Means Clustering method to find the optimal number of clusters to be around 4. This is theoretically consistent with our splitting of target variable labels into 4 groups for multi-label classification. I also appended cluster labels to the dataset as a feature in multi-label classification. 







Multi-Label Classification

Using the same hyper-parameter tuning and regularization with 10-fold cross-validation, LogisticRegression is giving accuracy scores of ~80% on training and ~70% on test data. 

Gradient Boosting overfit again.  



## Visualizations

Utilizing Plotly for interactive graphical visualizations, displayed the results for both Binary and Multi-label Classification. <Link to Plotly visualizations here>. 

Hover over any city to view its Actual vs. Predicted mobility label. Note the higher accuracy of the model, the more identical the map colors will be. 
























## Conclusions

Our hypothesis is confirmed that using data on community-level attributes, we can predict the level of future socioeconomic mobility of children who grow up in that community. This shows not only that there are geographical variations in the likelihood of the success of children, but also the community-level features which are most important in determining this. 

We can identify who is disadvantaged or advantaged, why, and hopefully how to help more children rise up. Once able to identify the factors helping or preventing children’s success in rising out of poverty, we can start to use this information to inform social policy, community activism, education reform, and targeted solutions for communities across the country.












