![alt text](https://drive.google.com/uc?id=1Tkiy1Gvc4Ce0L3qiHKUAvkttcWkGMU8O)

                                                                      Image source: https://vc4a.com/ventures/sendy-limited/

# **Sendy Explore Competition - Regression Analysis**

Team 2 - Mangaliso Samuel Makhoba, Bryan Green, Michael Ilic, Lawrence Hlapa, Faatimah Mansoor 
**The structure of this notebook is as follows:**

[**1 Introduction**](##1-introduction)


[**2 Body**](##2-body)

>[2.1 Import modules](#21-import-modules)

>[2.2 Import dataset](#22-import-dataset)

>[2.3 EDA](#23-eda)

>[2.4 Modelling](#24-modelling)

>[2.5 Model selection](#25-model-selection)

>[2.6 Analysis](#analysis)

[**3 Conclusion**](#3-conclusion)

[**4 References and links**](#4-references-and-links)

## 1. Introduction

Sendy is a logistic company in Kenya. The aim of this project is to build a regression model for Sendy which can accurately predict delivery time, from the time a package is picked up to its arrival at the final destination.

To build this model, the Train dataset and the riders dataset will used. Regression models will be trained, and the most suitable will be selected. This model will then be used to predict delivery time for the test dataset 

## 2. Body


### 2.1 Import modules

  Modules to be imported in jupyter notebook:
      import modules 
      import numpy as np 
      import pandas as pd
      import matplotlib.pyplot as plt 
      %matplotlib inline 
      import seaborn as sns
      import plotly.express as px
      import math

### 2.2 Dataset

##### Description of files in datasets:

  * Train - Dataset training our model
  train = pd.read_csv('/content/Train.csv')
  
  * Test - Dataset testing our model (y variables to be predicted)
  test = pd.read_csv('/content/Test.csv')
  
  * Riders - Riders info
  riders = pd.read_csv('/content/Riders.csv')
  
  * Variable Definitions - Info about columns and there values  
  variable_def = pd.read_csv('/content/VariableDefinitions.csv')
  
  * Sample - Sample results of competition
  sample = pd.read_csv('/content/SampleSubmission.csv')
  
  NB: We used jupyter notebook to run codes to import.

### 2.3 EDA

#### Categorical variables

  - Vehicle type (although there is only one - "bike")
  - Platform type
  - Personal or Business, referring to the business type
  - Date and day - however they should be represented as cyclical 
  
#### Ratio variable

  - Temperature
  
#### List of graphs created to explore data included in our notebook:

  - Figure 1. Number of missing values: null values per variable in the 'train' dataset.
  - Figure 2. Temperature distribution: temperature distribution from the'train'      dataset.
  - Figure 3. Overall data distribution: distribution of each of the variables in the 'train' dataset, including the y variable (Time from pickup to arrival)
  - Figure 4. Checking correlations: correlations heat map for the variables in the 'train' dataset.
  - Figure 5. Time from pickup to arrival: graphical representation of the distribution of pickup location.
  
  ### 2.4 Modelling
  
  #### 2.4.1 Preprocessing
  
  We started by analyzing the data and finding the columns that had too many missing values, or had no relevance to the final prediction.
  
  #### 2.4.2 Splitting data
  
  The next step was to split the data into the train and test sets, in order to prevent overfitting and to validate the effectiveness of the model.
  
  #### 2.4.3 Applying a cleaner function
  
  We built a custom cleaner function to drop nulls and format the data in a way that made it usable for model training.
  
  #### 2.4.4 Cross validation
  
  We applied cross validation to confirm that the data was valid and finally ready for training. 
  
  #### 2.4.5 Model pipeline
  
  Linear, Lasso and Ridge Regression
  Decision Tree Regressor
  Random Forest, Gradient Boosting, Bagging, AdaBoost Regressors
  XGB, LGBM, Cat Boost Regressors

### 2.5 Model selection

The moment we’ve all been waiting for!

We trained 6 different regression models and discovered that CatBoostRegressor returned the highest score, with a value of 720.82.

### 2.6 Analysis

- RMSE was used to select the best model 
- CatBoostRegressor provided the best RMSE score of 720.82
- We found that temperature had no effect on the delivery time

## 3. Conclusion

After testing 6 different models, CatBoostRegressor proved to be the most effective at accurately predicting delivery time.








  
  
  
  
  
  
  


  

