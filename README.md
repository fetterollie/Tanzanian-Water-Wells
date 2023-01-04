![header](images/header.jpg)
# Tanzanian-Water-Wells
## Navigating the Notebook
### Some things worth noting:
#### Work on this notebook was performed in two seperate environments:
1. The notebook in the main file uses the environment found in environment.yml 
2. The notebook used for mapping in the geopandas file uses the environment found in geoenvironment.yml
## Overview
## Business Understanding and Business Problem
Build a classification model to predict whether a pump is functional, needs some repairs, or doesn't work at all. Data driven predictions will lead to more efficient maintenance operations and will ensure clean and potable water is available to communities across Tanzania. 
### Cost of Errors
Tanzania has an area of 364,900 mi² which makes it the 30th largest country in the world. According to [trade.gov](https://www.trade.gov/country-commercial-guides/tanzania-construction), the managed national road network consists of 21058 miles of roadway, comprising 7944 miles of trunk and 13114 miles of regional roads. Due to the size of the country and the condition of infrastructure, it is important to only deploy maintenance and repair efforts to the locations that are positively in need of repair. 

Constructing a well in Tanzania can cost upwards of $10000 ([The Living Water Project](https://www.livingwaterwells.org/faqs)) depending on factors such as:
- cost of goods and labor
- necessary drilling depth
- amount of rock to drill through
- location of well
- cost of fuel (drilling and transportation)

Pumps in wells generally last 10 or more years but their parts do have a finite life span. The cost of repairing a well can range from a few hundred dollars to several thousand dollars. Sending repair efforts to wells that are predicted to need repairs but are in fact functioning (a false negative) use costly resources that could be put toward the wells that are actually in need of repair. 
## About the Data
Data for this project is from [Taarifa](http://taarifa.org/) and the [Tanzanian Ministry of Water](http://maji.go.tz/).
## Functions/Classes
This section houses functions and classes created to help later on in the notebook.
## Pipelines & Transformers
This section houses pipelines and transformers created to help later on in the notebook.
## Data Understanding
Length of DataFrame: 59400
### About the columns:
amount_tsh - Total static head (amount water available to waterpoint)<br>
date_recorded - The date the row was entered<br>
funder - Who funded the well<br>
gps_height - Altitude of the well<br>
installer - Organization that installed the well<br>
longitude - GPS coordinate<br>
latitude - GPS coordinate<br>
wpt_name - Name of the waterpoint if there is one<br>
num_private - <br>
basin - Geographic water basin<br>
subvillage - Geographic location<br>
region - Geographic location<br>
region_code - Geographic location (coded)<br>
district_code - Geographic location (coded)<br>
lga - Geographic location<br>
ward - Geographic location<br>
population - Population around the well<br>
public_meeting - True/False<br>
recorded_by - Group entering this row of data<br>
scheme_management - Who operates the waterpoint<br>
scheme_name - Who operates the waterpoint<br>
permit - If the waterpoint is permitted<br>
construction_year - Year the waterpoint was constructed<br>
extraction_type - The kind of extraction the waterpoint uses<br>
extraction_type_group - The kind of extraction the waterpoint uses<br>
extraction_type_class - The kind of extraction the waterpoint uses<br>
management - How the waterpoint is managed<br>
management_group - How the waterpoint is managed<br>
payment - What the water costs<br>
payment_type - What the water costs<br>
water_quality - The quality of the water<br>
quality_group - The quality of the water<br>
quantity - The quantity of water<br>
quantity_group - The quantity of water<br>
source - The source of the water<br>
source_type - The source of the water<br>
source_class - The source of the water<br>
waterpoint_type - The kind of waterpoint<br>
waterpoint_type_group - The kind of waterpoint<br>
### Joining Original DataFrame with Target
The original DataFrame did not include the target column, 'status_group' so the original data and the target data needed to be joined.
### Addressing Null Values
Each column with null values was assessed to see if missing values could be imputed or if the column needed to be dropped. The only column of concern is 'scheme_name'. 47.42% of values were missing. 
## Columns to Drop
'date_recorded' - not relevant to model</br>
'wpt_name' - not relevant to model</br>
'num_private' - not relevant to model</br>
'subvillage' - not relevant to model</br>
'region_code' - similar info to region</br>
'district_code' - similar info</br>
'lga' - similar info</br>
'recorded_by' - not relevant to model</br>
'scheme_name' - not relevant to model</br>
'funder' - not relevant to model</br>
'extraction_type_group' - duplicate info</br>
'extraction_type_class' - duplicate info</br>
'management_group' - duplicate info</br>
'payment_type' - duplicate info</br>
'quality_group' - duplicate info</br>
'quantity_group' - duplicate info</br>
'source_type' - duplicate info</br>
'source_class' - duplicate info</br>
'waterpoint_type_group' - duplicate info</br>
'status_group' - this is the target</br>
### Modifying Target
This will make the problem into a binary classification, reducing complexity in the models.
## Exploratory Data Analysis
||| need to insert eda stuff here
## Baseline Model
|||address how to say how well the model is performing...
The baseline model, predicting all wells as functional performed at ~54% ± 0.00007 accuracy. 
## First Simple Model
### Logistic Regression
### Decision Tree Classifier
### Random Forest Classifier
## Model Choice - Logistic Regression
1. Logistic regression is faster to train than other models
2. Logistic regression is more interpretable which makes it more useful for the non-technical presentation
3. Logistic regression is less prone to overfitting
### GridSearchCV
GridSearchCV is used to find the best hyperparameters for the chosen logistic regression model.
 - Best Strategy for imputing numericals: mean
 - Best C value: 1.0
 - Best penalty: l2
 - Best solver: liblinear
## Final Model - Logistic Regression
||| insert some notes about how this final model performs
||| insert some graphs maybe confusion matrix about how model performs
## Further Exploration/Questions
||| update once I finish this section in the notebook.
