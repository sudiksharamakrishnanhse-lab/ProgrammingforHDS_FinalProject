# ProgrammingforHDS_FinalProject
Final Project for Programming in HDS Class

**Predicting Sleep Disorders from Lifestyle and Health Data**

Dataset -	Sleep Health and Lifestyle Dataset

Source URL - https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset

File - Sleep_health_and_lifestyle_dataset.csv

Why this dataset was selected: 
1. It meets the technical requirements. About 374 records and 11 predictors, with a clear path to a binary target. Recoded outcome variable for binary classification.
2. The question is meaningful. Sleep disorders are common and often undiagnosed, so screening from routine data is a practical question.


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
