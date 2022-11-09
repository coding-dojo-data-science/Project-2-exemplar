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
