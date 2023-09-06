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

