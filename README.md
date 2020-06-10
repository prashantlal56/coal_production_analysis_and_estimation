# US State coal production Analysis and estimation for year 2018

The U.S. Energy Information Administration (EIA) is a principal agency of the U.S. Federal Statistical System responsible for collecting, analyzing, and disseminating energy information to promote sound policymaking, efficient markets, and public understanding of energy and its interaction with the economy and the environment. EIA programs cover data on coal, petroleum, natural gas, electric, renewable and nuclear energy. EIA is part of the U.S. Department of Energy.

EIA conducts a comprehensive data collection program that covers the full spectrum of energy sources, end uses, and energy flows; generates short- and long-term domestic and international energy projections; and performs informative energy analyses


The U.S. Energy Information Administration’s (EIA) Form EIA-7A, Annual Survey of Coal Production and Preparation, collects coal
production data from U.S. coal mining companies. This includes information on the type and status of coal operations, characteristics of
coalbeds mined, recoverable reserves, productive capacity and the disposition of coal mined which provides Congress with basic
statistics concerning coal supply. These data appear in the Annual Coal Report, the Quarterly Coal Report, the Monthly Energy Review, and
the Annual Energy Review. In addition, the EIA uses the data for coal supply analyses and in short-term modeling efforts, which produce
forecasts of coal supply and prices requested by Congress. The forecast data also appear in the Short-Term Energy Outlook and the Annual
Energy Outlook.

* ### My effort  
I have collected data in the form of excel sheet, did a deep analysis of last 5 years coal production. Found some usefull insight, understood the trend of coal production and at last build a model to predict coal production for year 2018 

## Project Overview

* Collected last 5 years dataset 
* Concatenating to one dataframe  
* Did exploratory data analysis to get the insight from data  
* Feature engineered some of the columns  
* Cross Validation among different models  
* Building model  
* Hypertuning the parameters and rebuilding the model 
* Prediction for year 2018

## Code and Resources Used
  **Python Version** : 3.8  
  **Packages** : pandas, numpy, sklearn, matplotlib, seaborn, plotly, cufflinks, xgboost, math   
  **Article** : [https://en.wikipedia.org/wiki/Energy_Information_Administration] [https://www.eia.gov/]  
  **Dataset** : [https://www.eia.gov/coal/data.php#production]  
  
  With each dataset we get the followings :  
 
  1.    MSHA ID                     
  2.    Mine Name                  
  3.    Mine State                 
  4.    Mine County               
  5.    Mine Status               
  6.    Mine Type                  
  7.    Company Type              
  8.    Operation Type            
  9.    Operating Company         
  10.   Operating Company Address   
  11.   Union Code                 
  12.   Coal Supply Region         
  13.   Production (short tons)   
  14.   Average Employees          
  15.   Labor Hours          
 
   ## Exploratory Data Analysis
   I went through distribution of numeric variables and frequency labels of different categorical variables. Found the relationship between different variables among themselves, made pivot tables and ploted graphs 
   
   Few key highlights of my findings :
    
![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/1.png)
![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/2.png)

* There is a continuous fall in coal production from year 2014 up untill year 2016 and after that a rise in production is seen in year 2017  
* There is fall in labor hour in year 2015 but after that it increases till year 2017  
* The only thing increases in year 2015 is average number of employees and than it decreases and again increases  
* The rate of percent increase is greater than that of percent decrease  
* The demand of coal has increased in year 2017. It may be either more new industries setups or increase of demand indirect products.  

![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/3.png)
![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/4.png)

* From year 2013 upto year 2015 active mine count decreases from 70.3% to 62.1% and in year 2016 an increase upto 76.2% even though year 2016 had a largest drop in production rate.
* We still have non producing active mines but it is good to see that their counts have decreased year wise.
* In year 2016, total Temporarily closed and Permanently abandoned mines were 11.83% which is less than previous year

![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/5.png)

## Feature Engineering  

Feature engineering steps I performed :  

* Rare label encoding of categorical variables by keeping the threshold to 0.05  
* Get dummy columns for categorical variables  
* Log transformation of continuous variables to make the variable distribution close to gaussian distribution.   

## Cross Validation
Performed 10 fold cross validation with average root mean square error as scoring parameter among 3 different models  
#### Models with average root mean square error :
* **Random Forest Classifier** - 0.8021447522773479   
* **Gradient Boosting Classifier** - 0.8041272547109883  
* **XGB Classifier** - 0.7895897018480074  

![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/rmse.png)  

#### Snice Xgb regressor gives the least average root mean square error, therefore we choose Xgb boost algorithm for model building

## Model Building
 With engineered dataset I trained the model and evaluated them using Root Mean Square Error. I choose RMSE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

### Model performance
* **Root Mean Square Error** : 0.7724259081122175  
* **R square score** : 0.8859696826855755  

## Tuning Hyper parameters and rebuilding the model

### Best Parameters are  
* Total number of tree in each iteration : 150  
* Learning rate : 0.1  
* Maximum depth of the Tree : 6  
* No sub sampling of the data set is best  

### Model performance with tuned parameters   
* Root Mean Square Error : 0.7492122006847867  
* R square value : 0.892720596313319  

## Prediction for year 2018
Before predicting coal production for year 2018, I preprocessed the 2018 coal production data set

![alt text](https://github.com/prashantlal56/coal_production_analysis_and_estimation/blob/master/Project_pics/pred.png)
