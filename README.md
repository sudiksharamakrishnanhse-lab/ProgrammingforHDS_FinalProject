# ProgrammingforHDS_FinalProject
Final Project for Programming in HDS Class

**Predicting Sleep Disorders from Lifestyle and Health Data**
This project builds and evaluates binary classification models that predict whether a person has a sleep disorder (insomnia or sleep apnea) from routine demographic, lifestyle, and vital-sign data.

1. Project Overview

**Background** Sleep disorders such as insomnia and sleep apnea are common and are associated with cardiovascular, metabolic, and mental-health problems, yet many cases are never formally diagnosed.
**Prediction Problem** The project predicts whether a person has a sleep disorder from age, gender, occupation, sleep duration, sleep quality, physical activity, stress level, BMI category, blood pressure, heart rate, and daily steps.
**Target Variable** Has Sleep Disorder` is binary (1 = Sleep Apnea or Insomnia, 0 = None)

2. Data Selection

**Dataset** Sleep Health and Lifestyle Dataset
**Source URL** https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset 
**File**  `Sleep_health_and_lifestyle_dataset.csv` (374 rows, 13 columns) 
**How it is loaded**  Upload prompt in the notebook (Section 1A) 
**Why it was selected.** The dataset meets the size and feature requirements, mixes numeric, ordinal, and categorical variables, and uses interpretable features (stress, activity, BMI, blood pressure).

3. Requirements and Dependencies

**Platform.** The notebook is designed for Google Colab. The notebook can also run in a local Jupyter environment with Python 3.10 or later.
**Packages** Packages needed if using a local Jupyter notebook are listed in `requirements_finalproject.txt`. This can be downloaded and installed.
**Jupyter notebook specific** If using a local Jupyter notebook, one line needs to be replaced in the file upload cell (Section 1A). The collab upload prompt (uploaded = files.upload()) is replaced with (filename = "Sleep_health_and_lifestyle_dataset.csv"). Make sure to put the data csv file in the same path as the Jupyter notebook. 


3. Execution Instructions
  
1. Open Github repo (https://github.com/sudiksharamakrishnanhse-lab/ProgrammingforHDS_FinalProject/tree/main) and download `Sleep_health_and_lifestyle_dataset.csv`, `requirements_finalproject.txt`, and `FinalProject_ProgrammingforHDS_SR.ipynb`
2. Open Google Colab and load the notebook with **`Sleep_health_and_lifestyle_dataset.csv`, then Upload notebook**. 
3. All cells are run in order with **Runtime, then Run all** (or one at a time from top to bottom).
4. At Section 1A, the run pauses and a **Choose Files** button appears. The file `Sleep_health_and_lifestyle_dataset.csv` is selected, and the run continues after the upload completes.
5. The remaining sections run without further input. The whole notebook takes roughly 40 seconds to 1 minute to fully run. 

4. Dataset Exploration 
- Import into Google Colab: Section 1A (upload prompt) 
- Dataset structure: Section 1B (`df.info()`) 
- Target variable: Section 2 (`Has Sleep Disorder`) 
- Predictor variables: Table below 
- Descriptive statistics: Section 3 (describe, variance, IQR, skewness, category counts, target balance) 
- Exploratory visualizations: Section 4 (sleep disorder status by BMI category, sleep duration histogram, Phi-K correlation heatmap covering numeric and categorical variables)
- Inferential analysis: Section 5 (Mann-Whitney U test and chi-square test)

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


5. Project Planning & Notebook Outline

**Evaluation Metrics**
- Recall (sensitivity): In screening, a missed case costs more than a false alarm.
- F1-score: Balances recall against precision.
- ROC-AUC: Threshold-independent measure of separation.
- Precision, specificity, balanced accuracy, MCC, PR-AUC: Show how the model handles false alarms.
- Accuracy: Can mislead if classes are uneven.



5. Pipeline Enhancements
6. Key Findings & Intepretation
7. Limitations
8. Execution Instructions




Potential Challenges 
1. Small sample size- Performance estimates are unstable
2. Self-reported variables. Sleep quality and stress are subjective ratings.
3. Combining two disorders. Insomnia and sleep apnea have different causes, so merging them may skew some results 
