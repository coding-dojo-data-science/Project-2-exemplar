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
![image](https://user-images.githubusercontent.com/18369971/200953273-2cee6eab-aa38-4617-9bca-07542a1e2b17.png)

- Normalized distribution shows the trend that older patients are more likely to have a stroke than younger patients.

![image](https://user-images.githubusercontent.com/18369971/200953803-c858831b-b449-4ef4-9c9e-f684e839de66.png)

- The average BMI in the dataset is 29. A majority of the dataset contains patients that are considered 'Overweight' or 'Obese'. 
- BMI and age has a slightly positive trend.
- Age is clearly a determining factor in stroke outcome with most strokes occurring over the age of 40. 

![image](https://user-images.githubusercontent.com/18369971/200954022-44c57b22-4046-4325-be86-d7b94fdc3587.png)
- Older patients have much higher avg_glucose_levels compared to younger patients. 

- High BMI and high glucose levels surprisingly have a lower impact on stroke outcome as originally thought. 

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

### Recommended Model

**The Tuned XGBoost Model** is recommended due to it have the highest recall across all of the models while maintaining a similar accuracy as other models with higher recall scores. 
This model will lead to overdiagnosis of stroke outcomes, however, the downside to this is less than if the model missed stroke diagnosis's. 

#### Stroke Detection

The primary predictor to a stroke will be the patient's age. Secondary concerns include: heart disease, glucose levels, and BMI. Patients that have heart concerns and/or are overweight or obese, especially if the patient is older, should visit a doctor to help guide them towards healthier options in order to reduce the risk of stroke as much as possible. 
