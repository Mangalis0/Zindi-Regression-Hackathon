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

>[2.6 Using model on Test](#26-using-model-on-test)

>[2.7 Functions to be placed in API](#functions-to-be-placed-in-api)

[**3 Conclusion**](#3-conclusion)

[**4 References and links**](#4-references-and-links)

## 1. Introduction

Sendy is a logistic company in Kenya. The aim of this project is to build a regression model for Sendy which can accurately predict delivery time, from the time a package is picked up to its arrival at the final destination.

To build this model, the Train dataset and the riders dataset will used. Regression models will be trained, and the most suitable will be selected. This model will then be used to predict delivery time for the test dataset 

## 2. Body


### 2.1 EDA

*Categorical variables

   Vehicle type(although there is only one- bike)
   Platform type
   Personal or Business, referring to the business type
   Date and day - however they should be represented as cyclical
   
*Ratio variable 
   Temperature 


Models
import modules 
import numpy as np 
import pandas as pd
import matplotlib.pyplot as plt 
%matplotlib inline 
import seaborn as sns
import plotly.express as px
import math

###2.2 Import dataset

#if using google colab,run this cell to import data 
train = pd.read_csv('/content/Train.csv') #training set
test = pd.read_csv('/content/Test.csv') #testing set(y variable to be predicted)
riders = pd.read_csv('/content/Riders.csv') #riders info
variable_def = pd.read_csv('/content/VariableDefinitions.csv')
sample = pd.read_csv('/content/SampleSubmission.csv') #sample of competition submission, should have order no for testing set, and y predicted from model


#if using jupyter notebook, run this cell to import data
train = pd.read_csv('Train.csv') #training set
test = pd.read_csv('Test.csv') #testing set(y variable to be predicted)
riders = pd.read_csv('Riders.csv') #riders info
variable_def = pd.read_csv('VariableDefinitions.csv')
sample = pd.read_csv('SampleSubmission.csv') #sample of competition submission, should have order no for testing set, and y predicted from model

###2.3 EDA

**Variable** **definitions**

variable_def

**Riders EDA**

riders.head()

riders.info()

riders.isnull().sum(axis = 0) #number of nulls per column 


# Riders Number Of Ratings Vs Number Of Orders

from matplotlib import rc

rc('mathtext', default='regular')
# Create Empty figure
build = plt.figure(figsize=(22,15))

# Split Figure To Allow Two Sets Of Y Axes
axes1 = build.add_subplot(111)

# Plot The First Line On Its Axis
axes1.plot(np.arange(len(riders["No_of_Ratings"])), riders["No_of_Ratings"], '-', label = "No_of_Ratings", color='red')

# Create Second Y Axis And Plot Second Line
axes2 = axes1.twinx()
axes2.plot(np.arange(len(riders["No_Of_Orders"])), riders["No_Of_Orders"], '-', label = "No_Of_Orders")

# Add Legends For Each Axis
axes1.legend(loc=2)
axes2.legend(loc=9)

axes1.grid()

# Set Labels Of Axes
axes1.set_xlabel("Riders")
axes1.set_ylabel("Number Of Ratings")
axes2.set_ylabel("Number Of Orders")
plt.show()



