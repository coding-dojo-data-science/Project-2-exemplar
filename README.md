# Stroke Prediction Project
- Name: Tyler Schelling
- Date Started: 11/2/2022

## Project Description
Stroke dataset will be used to understand correlations across stroke patients and creating a model to predict strokes.

## What is a Stroke?
Per the [CDC](https://www.cdc.gov/stroke/about.htm#:~:text=A%20stroke%2C%20sometimes%20called%20a,term%20disability%2C%20or%20even%20death.), a stroke occurs when something blocks blood supply to a part of the brain or when a blood vessel in the brain bursts. 
In either case, parts of the brain become damaged or die. A stroke can cause lasting brain damage, long-term disability, or even death. 

## Dataset Information
The dataset was found on [Kaggle](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset?datasetId=1120859&searchQuery=eda). 

### Data Dictionary
Column Name | Description
---|---
id | Unique identifier
gender| 'Male', 'Female', or 'Other'
age| Age of the patient
hypertension | 0 if patient doesn't have hypertension, 1 if the patient has hypertension
ever_married | 'No' or 'Yes'
work_type | 'children', 'govt_job', 'never_worked', 'private', or 'self-employed'
Residence_type | 'Rural' or 'Urban'
avg_glucose_level | average glucose level in blood
bmi | body mass index
smoking_status | 'formerly smoke', 'never smoked', 'smokes', or 'unknown'
stroke | 1 if the patient had a stroke or 0 if not

### Feature Correlation to Stroke Outcome
![image](https://user-images.githubusercontent.com/18369971/200951596-ffc284f1-d833-4fa5-bb9b-fb051b44cfd9.png)

Overview of all features and their correlation to predicting a stroke outcome. 
Top Features:
- Age
- Heart Disease
- Avg Glucose Level
- Hypertension
- Ever Married

### Explanatory Data Analysis
![image](https://user-images.githubusercontent.com/18369971/206331916-715dcac5-e364-432b-8b44-0b3fa46c2055.png)

![image](https://user-images.githubusercontent.com/18369971/206331751-565b72cb-202e-4282-ae99-a43b792bdbd7.png)

![image](https://user-images.githubusercontent.com/18369971/206331805-99908fbb-7773-4196-ba70-3b57b9d0ba65.png)

![image](https://user-images.githubusercontent.com/18369971/206331964-82f0b426-62b3-48a7-b7c2-acdedd6e925d.png)

### Model Evaluation

During model evaluation, reducing the count of type 2 errors (false negatives) will be the priority. 
Type 2 Error (False Negative): If a model predicts that an individual will not have a stroke outcome, but in reality they will, this is a false negative. Ideally, we will want to minimize the number of false negatives we experience even if that lowers the overall accuracy of the model. 

Model	|Accuracy Score|	Precision Score	|Recall Score|	F1 Score|	ROC	|Execution Time
---|---|----|----|----|----|---
Decision Tree|	0.881754	|0.161905|	0.2125	|0.183784	|0.569491	|	0.20
Random Forest|	0.911511	|0.097561	|0.0500	|0.066116	|0.509545|	1.01
Logistic Regression|	0.745497|	0.162534|	0.7375|	0.266366|	0.741766	|	0.21
KNeighbors|	0.830070|	0.145078	|0.3500	|0.205128|	0.606078	|	0.53
ADA Boost|	0.805012|	0.171206|	0.5500	|0.261128|	0.686028	|	0.57
Light GBM|	0.907596|	0.068182	|0.0375|	0.048387|	0.501624	|	0.67
XGBoost|	0.861394|	0.183007	|0.3500	|0.240343|	0.622786	|	0.76
Gradient Boosting	|0.870008	|0.192857	|0.3375|	0.245455|	0.621549	|	1.59
Logistic Regression Tuned|	0.736100	|0.159151	|0.7500	|0.262582|	0.742586|	23.97
Logistic Regression Tuned|	0.736100|	0.159151	|0.7500	|0.262582|	0.742586	|20.55
ADA Boost Tuned	|0.775255|	0.177570|	0.7125|	0.284289|	0.745974	|	208.06
XGBoost Tuned|	0.740016|	0.173575|	0.8375	|0.287554|	0.785500|	191.41
Logistic Regression PCA Tuned|	0.747847|	0.163889|	0.7375	|0.268182|	0.743019|	17.39
ADA Boost PCA Tuned|	0.751762|	0.152493	|0.6500|	0.247031	|0.704282	|	280.25
XGBoost PCA Tuned	|0.740016|	0.170157|	0.8125|	0.281385	|0.773836	|	207.15

Recall Score and ROC will be the primary scores that will impact the recommended model. 

- Charting all models based on recall score shows the following:
![image](https://user-images.githubusercontent.com/18369971/206332020-90cd9d45-76f5-4728-8a68-7584423054d6.png)

### Recommended Model

**The Tuned XGBoost Model** is recommended due to it have the highest recall across all of the models while maintaining a similar accuracy as other models with higher recall scores. 
This model will lead to overdiagnosis of stroke outcomes, however, the downside to this is less than if the model missed stroke diagnosis's. 

![image](https://user-images.githubusercontent.com/18369971/206332078-f2492698-db8e-40eb-b126-27f18a25a4b4.png)

- Minimizing the false negatives will be the most beneficial for the insurance company.
- Incorrectly predicting patients will not have a stroke when they actual do (false negative) can be costly to the company and does not provide adequate resources for preventative care to patients. 
- The downside to this model is the high rate of false positives. However, providing additional preventative care to patients that are likely not going to have a stroke will still be more cost effective than having a higher false negative rate.  

#### Stroke Detection

The primary predictor to a stroke will be the patient's age. Secondary concerns include: heart disease, glucose levels, and BMI. Patients that have heart concerns and/or are overweight or obese, especially if the patient is older, should visit a doctor to help guide them towards healthier options in order to reduce the risk of stroke as much as possible. 

### Recommendations
- The tuned XGBoost model can lead to catching at risk patients early to provide the necessary preventative care and/or treatment.
- False negatives are still a risk in the model and some predictions may require mild manual review in order to potentially catch any concerns not captured by the predictive model. 
- Aging patients, especially those with heart disease and/or hypertension, should seek medical care to get the appropriate preventative care with a medical professional. 

