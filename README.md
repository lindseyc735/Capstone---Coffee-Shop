# Springboard Capstone Project: Coffee Shop

Starbucks is getting a run for its money. While they are still renowned for having a coffee shop on every corner, more coffee shop chains and local shops are opening. The competition is steep, and each chain or local shop needs something that sets them apart from the other competitors. My goal for this project was to identify the top coffee features a new coffee shop would need to consider when creating its signature blend to set it apart from Starbucks and other coffee shops.

As the project unfolded, I utilized the following python packages:

- numpy
- pandas
  - ProfileReport from pandas_profiling
- matplotlib.pyplot
- seaborn as sns
- display from IPython.display
- os
- sklearn.preprocessing
  - StandardScaler
- sklearn.model_selection
  - train_test_split
  - GridSearchCV
- sklearn.linear_model
  - LinearRegression
  - ElasticNet
- sklearn.ensemble
  - RandomForestRegressor
- sklearn.svm
  - SVR
- sklearn.metrics
  - make_scorer
  - mean_squared_error
  - mean_absolute_error 
- xgboost
- shap

## Data Sourcing and Cleaning 

Data for this project was sourced from Kaggle. The data set comprises reviews collected on a website, rating coffees by features, and providing other descriptive information such as origin, roaster, and other notes. There were a total of 19 features and 7,041 entries. The original data set can be found [here](https://www.kaggle.com/datasets/patkle/coffeereviewcom-over-7000-ratings-and-reviews).

Viewing the first 5 rows of the dataset, I already noticed features with missing values. In order to better determine how to process missing values, I called a count of null values on each feature. The results are displayed below.

![Null Values Count]()

The 'with_milk' feature was immediately dropped due to having nearly 86% null values. I considered dropping the 'agtron' feature also, since 257 of its entries were a simple '/' without any numeric features. With some research, I found that the agtron score is rating the coffee beans before and after grinding. Since this has a possible affect on the overall rating, I left this feature for now.

According to the display of the first 5 rows, 'rating' was based on a 1-100 scale, while 'acidity_structure', 'aftertaste', 'aroma', 'body', and 'flavor' were all based on a 1-10 scale. Whichever range, all these categories should be numeric, but were currently labeled as objects. I changed these categories to numeric categories, and confirmed every category was either numeric for a rating or an object for a descriptive feature.

## EDA

To more extensively explore the data, I ran a ProfileReport. The report gave 28 alerts regarding features with high cardinality, features with high correlation, features with missing values, uniformly distributed features, and features with completely unique entries. The report also gives a summary of each feature, visualizations, as well as notes features that are unique, common, rare, most frequent, and least frequent. I used this report to determine which features needed further cleaning.

### Features to Drop

The report showed several features that ended up needing to be dropped from the useable data set. Several of these feautres were commentary rather than descriptive of the coffee itself, or had high percentages of null or unuseable data. The following features were dropped:

- acidity_structure _(high correlation with the rating category, but about 62% null values)_
- agtron _(high cardinality, empty rating frames, and alphabetic entries resulting in unuseable data)_
- est_price _($18.00/12 ounces was the most common entry, but only made up 2.2% of the data. This category may be useful for product pricing in a secondary project.)_
- Commentary features
  - title
  - blind_assessment
  - bottom_line
  - notes
  - review_date
  - url

### Features with Replaced Data

The following features had null values replaced. Numeric features with null values were replaced by the feature's rounded mean, and object features had null values and similarly formated entries replaced by the frequently used "Not disclosed". The features with replaced values are listed below:

- aftertaste
- aroma
- body
- flavor
- coffee_origin
- roast_level
- roaster_location

## Pre-Processing and Training

