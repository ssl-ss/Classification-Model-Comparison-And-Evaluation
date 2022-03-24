# Machine-Learning-Model-Selection-Evaluation-
Apply machine learning models (decision tree/logistic regression/svc) to find out factors that are most predictive of data scientists leaving their current job


## Objective

In this project, I am looking at what kinds of factors are most predictive of data scientists leaving their current job.
Practically, HRs in companies can use this information to predict if their employees are leaving and can take measures accordingly. 
Since the predicted outcomes are binary (i.e., leave or stay), this project will be a classification task. 

More importantly, in this project, I want to accomplish the whole process of building a machine learning pipeline in a systematic way. And be able to compare and evaluate different (classification) machine learning models. 

## Data

This dataset is from Kaggle (https://www.kaggle.com/arashnic/hr-analytics-job-change-of-data-scientists?select=aug_train.csv): 

<img width="471" alt="image" src="https://user-images.githubusercontent.com/58230771/159835761-5a6b7137-44fe-4b85-8588-b98fa3eff53c.png">


### Features ###

<img width="992" alt="Screen Shot 2022-03-23 at 10 32 33 PM" src="https://user-images.githubusercontent.com/58230771/159836777-7cf82009-3ac6-4340-b5d6-524427834ac0.png">
I used 9 features for model training. 2 of them were numerical and 7 of them were categorical. 
The classification target was labeled as either 0 or 1. 0 means the data scientists are looking for a job change while 1 means they are not.  

This dataset is very imbalanced. 14,381 samples belonged to the 0 class but only 4,777 samples belonged to the 1 class.  


## Data Preprocessing 

<img width="783" alt="image" src="https://user-images.githubusercontent.com/58230771/159839620-e608d4cb-a6e5-4e12-99ed-4df6d0314911.png">

#### Before: ####
<img width="552" alt="image" src="https://user-images.githubusercontent.com/58230771/159842754-d6d111e0-c0e1-4720-8a4c-b42c8608699e.png">

#### After: ####
<img width="552" alt="image" src="https://user-images.githubusercontent.com/58230771/159842775-34597dcf-5b6b-4449-b01e-abfe0846d1f8.png">



## Model Selection & Parameter Tuning 

I chose 3 commonly used classification models - Support Vector Classification, Decision Tree, and Logistic Regression - to make the prediction. For each classifier, I performed a grid search with 5-fold cross validation to find the sets of parameters that produce the best outcomes.  

The sets of parameters I tuned are the followings: 

<img width="833" alt="image" src="https://user-images.githubusercontent.com/58230771/159843584-eafa598c-8812-429f-b5d1-6a3ed1d0f45b.png">

