# Classification-Model-Comparison-And-Evaluation-
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
<img width="783" alt="image" src="https://user-images.githubusercontent.com/58230771/159842754-d6d111e0-c0e1-4720-8a4c-b42c8608699e.png">

#### After: ####
<img width="783" alt="image" src="https://user-images.githubusercontent.com/58230771/159842775-34597dcf-5b6b-4449-b01e-abfe0846d1f8.png">



## Model Selection & Parameter Tuning 

I chose 3 commonly used classification models - Support Vector Classification, Decision Tree, and Logistic Regression - to make the prediction. For each classifier, I performed a grid search with 5-fold cross validation to find the sets of parameters (highlighted in yellow) that produce the best outcomes.  

The sets of parameters I tuned are the followings: 

<img width="552" alt="image" src= "https://user-images.githubusercontent.com/58230771/160515604-0562d8f5-9832-4cf5-8f45-a48b95a64843.png">


## Results

### Metrics 
<img width="758" alt="image" src="https://user-images.githubusercontent.com/58230771/160519601-34321ddc-6196-409a-92a6-0f132eb70e9c.png">

Based on the key metrics, the SVC model outperformed the other two models. It had the highest accuracy/precision for identifying the positive class/recall/f1. Although its precision for classifying the negative class was lower than that of the Logistic Regression model, we are tolerant of the cost since we care more about correctly identifying the positive class. 


### ROC ###
(SVC)

<img width="600" alt="Screen Shot 2022-03-28 at 9 21 44 PM" src="https://user-images.githubusercontent.com/58230771/160519978-76b1159f-fd7d-45e3-8530-71f69a19ae40.png"> 

(Decision Tree)

<img width="600" alt="Screen Shot 2022-03-28 at 9 35 06 PM" src="https://user-images.githubusercontent.com/58230771/160521376-a400c025-0c68-412f-9fd9-7f9305f3e9eb.png">

(Logistic Regression) 

<img width="600" alt="Screen Shot 2022-03-28 at 9 43 28 PM" src="https://user-images.githubusercontent.com/58230771/160522427-86145190-e84f-4a71-9c94-4400de2aa00d.png">

AUC: SVC = LR > Tree

The AUC values also supported that SVC was a better model.  

### Feature Importance ###

(SVC)

<img width="427" alt="Screen Shot 2022-04-03 at 5 59 22 PM" src="https://user-images.githubusercontent.com/58230771/161452521-b5415a58-5a86-4221-84b4-b10f2150bfbd.png">

According to the SVC model, city_development_index, which is a numerical variable that shows how developed a city is, contributed the most to predict the data scientist would stay in the current company. In contrast, the enrolled_university variable, which has 3 cases: no enrollment, part-time enrollment, and full-time enrolment, was predictive of the data scientist was planning on a job change. 

(Decision Tree)

<img width="665" alt="image" src="https://user-images.githubusercontent.com/58230771/161453056-86e7ad13-d651-4c5a-ad6e-c0caa476cdb8.png">

Again, the city_development_index was still considered a very important predictor by the decision tree classifier. The next important variables were experience-related. 

(Logistic Regression) 

<img width="350" alt="image" src="https://user-images.githubusercontent.com/58230771/161453498-7bba6d7a-7e8e-4941-ab8a-6e2a1df3cbeb.png">

Similar to the SVC model, the Logistic Regression model thinks that the development index of the city was associated with data scientists staying. The last_new_job variable, which is the difference in years between previous job and current job, was predictive of data scientists leaving. 

#### Overall, all 3 models did a fairly good job in prediction although SVC performed slightly better than the other two. They all agreed that how developed a city is could determine if data scientists want to stay in their current job or not. 
