# House-Valuation
Use inadequate data features + geographical features to model and forecast house prices


## Background
In the usual case of house price forecasting, we use a large amount of housing-related information to make our forecasts. 
Sometimes geographical information is also used, and they are usually in the form of latitude and longitude.

In the dataset used for this project (the data is not publicly available at this time), we only have a small amount of house information, and a larger amount of geographical information. Moreover, it is easy to see that there seems to be a lot of overlap in what is expressed by this geographical information.



## File Description
*house pricer.ipynb*: Project code file. The notebook is exploratory in searching for data related to the problem shown in the notebook title. Markdown cells are used to help complete the various steps in the thinking process.

*Note that all the comments in this file is written in french.


## Features of data 
Transaction history: 
- 'id','date'

Geographic location:
- 'number', 'number_complement','type_voie','street'
- 'yanport_quarter','yanport_quarter_code', 'insee_code', 'city'
- 'zip_code'
- 'department'
- 'longitude', 'latitude'

House Infomation：
- 'rooms', 'area', 'outdoor_area'

Target: 
- 'price' / 'price_area'


## Feature Engineering
1. Deletion of features with a large number of null values
2. Using multiple geographic information, a new feature is constructed to mark whether a house is in a high house price area, based on trends in the geographical distribution of house prices.
![loc](https://user-images.githubusercontent.com/59653182/120941068-f0eee100-c720-11eb-9931-6a12f9fe5e2f.png)


## Preprocessing
1. Delete samples with null values
2. Normalisation of feature variables for skewing distribution 


## Modeling
Selection of models and parameters using grid search and cross-validation:
__________________________________________________________________________________
![image](https://user-images.githubusercontent.com/59653182/120941592-ba669580-c723-11eb-96cb-b2cc23605e41.png)
__________________________________________________________________________________

RMSE in training set:  0.5161856008856414 

RMSE in test set:  0.5615245239196881 

Best parameter set:  {'learning_rate': 0.01, 'max_depth': 3, 'n_estimators': 1000} 
__________________________________________________________________________________

## Results & Analysis
The use of RMSE to evaluate the regression model reveals that the errors obtained are large. This could be due to the lack of information related to the house (judging by logic, the value of the house still depends mainly on the characteristics of the house itself and not on geographical features).

In addition to this, during the feature processing, the correlation between postcodes and house prices was initially found to be high. The author later realised that this was due to the strong correlation between the serial number of the postcode and the geographical location in France (the serial number starts from the city centre and spirals outwards). However this does not necessarily hold in other countries, so the method of new eigenvalues is still of some reference value.

In addition to this, there are a number of other ways in which access can be gained to improve the presentation of the model. For example, new variables can indicate more house price classes than just binary categories (whether they are high house price areas).
