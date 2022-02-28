# Module 12 Report Template

## Overview of the Analysis

The Purpose of this analysis is to analyze the credit risk using a set of imbalanced borrower data to predict the "healthiness" of a loan. A healthy loan is one that will most likley get paid and an unhealthy loan is one that is in high risk of default. There has been two logistical regression classifier models that are created due to the nature of the data being imbalanced. The first model, also known as the original model is trained using original feature data. The second model is trained using the resampled data. These models will gice us predictions which then can be compared. 

Details of the Dataset 
* lending_data.csv was the only dataset used to analyze this space. This CSV file contained data such as ```loan_size | interest_rate | borrower_income | debt_to_income | num_of_accounts | derogatory_marks | total_debt | loan_status``` about the borrowers. In the model the ```loan_status``` column was used as the prediction value or the ```y```. The value of 0 signified a healthy loan and 1 signifying an unhealthy loan. 

Model Process
* First the lending_data.csv was split into two categories, training and testing, which included the y value sets from the loan_status column. Then a LogisticRegression model was created to fit with the original training data. This model then predicted using the original test data. The measurment tool that was used to measure prediction performance was ```balanced_accuracy_score```, ```confusion_matrix``` and ```classification_report```. Using the RandomOverSampler from the imbalanced learn module I was able to resample the original data. Additionally a second LogisticRegression model was created which then trained and fit the resampled data. This resampled model is then able to predict using the same_test_data. The resampled model's predictions will be evaluated with the same metrics: ```balanced_accuracy_score```, ```confusion_matrix``` and ```classification_report```. The performace metrics for each approach will then be compared. 

## Results

Original Data Model 
Below are the logistic regression model predictions, trained with the original unbalanced data: 

* ```0 - recall was .99 with a precision of 1```
* ```1 - recall was 0.85 with a precision of 0.85```
* ```.952 balanced accuracy score```

Classification Report Original 
![original](https://github.com/Oleener/Challenge_12_Credit_Risk/blob/main/Images/Original%20.png)

RandomOverSampler Data Model
Below are the logistic regression model predictions, trained with the resampled data: 

* ```0 - recall was .99 with a precision of 1```
* ```1 - recall was .99 with a precision of .84```
* ```.993 balanced accuracy score```

Classification Report Resampled 
![resampled](https://github.com/Oleener/Challenge_12_Credit_Risk/blob/main/Images/Resampled.png)

## Summary

Overall, after testing both of the models the data shows that they performed similarly with slight differences. Of the two predictions it looks like there is a higher importance in finding the ```1``` as it is the less common data point. This tells us that issuing a risky loan which has a possibilty of defaulting may be more costly than issuing a healthy loan. Therefore it may be best to choose a model which does a better job at predicting the ```1``` values. 

When comparing the two models, it looks like the resampled model has a higher recall value of ```0.99```, whereas the original model has a recall of ```0.91```. Additionally when looking at the precision of the resampled model there is a slight drop from ```0.85``` to ```0.84```. 

I would recommend using the resampled model which includes higher recall for the ```1``` value as this is an advantage over the model fit with original data. 
