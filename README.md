# ProgrammingforHDS_FinalProject
Final Project for Programming in HDS Class

**Predicting Sleep Disorders from Lifestyle and Health Data**
This project builds and evaluates binary classification models that predict whether a person has a sleep disorder (insomnia or sleep apnea) from routine demographic, lifestyle, and vital-sign data.

1. Project Overview

**Background** Sleep disorders such as insomnia and sleep apnea are common and are associated with cardiovascular, metabolic, and mental-health problems, yet many cases are never formally diagnosed.
**Prediction Problem** The project predicts whether a person has a sleep disorder from age, gender, occupation, sleep duration, sleep quality, physical activity, stress level, BMI category, blood pressure, heart rate, and daily steps.
**Target Variable** Has Sleep Disorder` is binary (1 = Sleep Apnea or Insomnia, 0 = None)

3. Data Selection

**Dataset** Sleep Health and Lifestyle Dataset
**Source URL** https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset 
**File**  `Sleep_health_and_lifestyle_dataset.csv` (374 rows, 13 columns) 
**How it is loaded**  Upload prompt in the notebook (Section 1A) 
**Why it was selected.** The dataset meets the size and feature requirements, mixes numeric, ordinal, and categorical variables, and uses interpretable features (stress, activity, BMI, blood pressure).

3. Dataset Exploration 
- Import into Google Colab: Section 1A (upload prompt) 
- Dataset structure: Section 1B (`df.info()`) 
- Target variable: Section 2 (`Has Sleep Disorder`) 
- Predictor variables: Table below 
- Descriptive statistics: Section 3 (describe, variance, IQR, skewness, category counts, target balance) 
- Exploratory visualizations: Section 4 (sleep disorder status by BMI category, sleep duration histogram, Phi-K correlation heatmap covering numeric and categorical variables)
- Inferential analysis: Section 5 (Mann-Whitney U test and chi-square test)


4. Project Planning & Notebook Outline
5. Pipeline Enhancements
6. Key Findings & Intepretation
7. Limitations
8. 



Variable Explanation

Predicator Variables
1. Gender: Categorical	Male / Female
2. Age: Numeric	Age in years
3. Occupation: Categorical	Person's profession
4. Sleep Duration: Numeric	Hours of sleep per day
5. Quality of Sleep: Ordinal	Subjective rating, 1 to 10
6. Physical Activity: Level	Numeric	Minutes of activity per day
7. Stress Level: Ordinal	Subjective rating, 1 to 10
8. BMI Category: Categorical (ordinal)	Normal, Overweight, Obese
9. Blood Pressure: Text	Stored as "systolic/diastolic" 
10. Heart Rate: Numeric	Resting heart rate in bpm
11. Daily Steps: Numeric	Steps per day

Target/Outcome Variable 

Original column: Sleep Disorder with values None, Insomnia, Sleep Apnea.

New binary target: Has Sleep Disorder

0 - No sleep disorder (Sleep Disorder = None)
1- Sleep disorder present (Sleep Disorder = Sleep Apnea or Insomnia)


Project Planning 

Proposed Prediction Problem: Can routinely available demographic, lifestyle, and vital-sign information be used to predict whether a person has a sleep disorder?

Preprocessing Steps
1. Drop Person ID and the original Sleep Disorder column from the predictors.
2. Standardize BMI category labels.
3. Split Blood Pressure into Systolic and Diastolic.
4. Scale numeric features for logistic regression, SVM, and KNN.
5. Recode Sleep Disorder Value as binary

Potential Challenges 
1. Small sample size- Performance estimates are unstable
2. Self-reported variables. Sleep quality and stress are subjective ratings.
3. Combining two disorders. Insomnia and sleep apnea have different causes, so merging them may skew some results 
