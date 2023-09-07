# Springboard Capstone Project: Coffee Shop

Starbucks is getting a run for its money. While they are still renowned for having a coffee shop on every corner, more coffee shop chains and local shops are opening. The competition is steep, and each chain or local shop needs something that sets them apart from the other competitors. My goal for this project was to identify the top coffee features a new coffee shop would need to consider when creating its signature blend to set it apart from Starbucks and other coffee shops.

## Data Sourcing and Cleaning 

Data for this project was sourced from Kaggle. The data set comprises reviews collected on a website, rating coffees by features, and providing other descriptive information such as origin, roaster, and other notes. There were a total of 19 features and 7,041 entries. The original data set can be found [here](https://www.kaggle.com/datasets/patkle/coffeereviewcom-over-7000-ratings-and-reviews). In the initial data wrangling stage I deleted a feature that was missing most of its data, reformated numeric entries reading as objects into numeric categories, and ran a number summary.

## EDA

To more extensively explore the data, I ran a ProfileReport. The report gave 28 alerts regarding features with high cardinality, features with high correlation, features with missing values, uniformly distributed features, and features with completely unique entries. The report also gives a summary of each feature, and visualizations, as well as notes features that are unique, common, rare, most frequent, and least frequent. I used this report to determine which features needed further cleaning.

### Features to Drop

The report showed several features that ended up needing to be dropped from the unusable data set. Several of these feautres were commentary rather than descriptive of the coffee itself or had high percentages of null or unusable data. These categories were dropped from the data set. Other features with missing values had the null values replaced with the feature's mean for numeric features, or "Not disclosed" for the object categories to standardize their null values.

## Pre-Processing and Training

The object features had high cardinality, so I created dummy variables. I also used StandardScaler to standardize the magnitude of the numeric features, and then fit and transform the data. The dummy variables and standardized numeric features were concatenated into the original data frame, the original features were dropped, and the resulting data was made into a pandas data frame. I used the train_test_split feature to split X (all features except for the target feature) and y (target feature 'rating' only) into an 80/20 train/test split.

## Modeling & Visualization

I ran Linear Regression, Random Forest, Extreme Gradient Boosting (xgboost), Support Vector Regression (SVR), and Elastic Net models with and without GridSearchCV() to optimize hyperparameters and determine the best model for this project. The models were evaluated by MAE, MSE, and RMSE. The xgboost model with GridSearchCV() proved to be the best model with the lowest MSE, RMSE, and second-lowest MAE of all the models. I visualized a Learning Curve graph showing that the test and training data sets were adequately trained, and used SHAP to visualize a summary plot, a summary bar graph, and a force plot. These visualize showed that flavor, aroma, body, and aftertaste were the features that most significantly impacted the overall rating. All other features had miniscule impact. So, I dropped all but the flavor, aroma, body, aftertaste, and rating features and ran xgboost with GridSearchCV() on the new data set. I evaluated the model with the same metrics as I did with the original data set modeling. I created a metric file to compare the original and reduced data set modeling. As it turns out, the original data set had slightly better metrics than the reduced data set. I still visualized the Learning Curve, SHAP summary bar graph, summary plot, and force plot for a visual comparison of the two data sets. 

## Next Steps

I would recommend completing a project to gather data and determine exactly what description of flavor, aroma, body, and aftertaste results in the highest ratings. More data will need to be gathered, as the data for this project originally scaled these features on a 1-10 range rather than a descriptive scale. Another project could also be done to help set a quantity and sale price.
