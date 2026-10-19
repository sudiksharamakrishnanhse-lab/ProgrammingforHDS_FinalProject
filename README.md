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

3. Repository Contents
- `FinalProject_ProgrammingforHDS_SR.ipynb`: The analysis notebook (all of the code, explanations, and interpretations)
- `README.md`: This document
- `Sleep_health_and_lifestyle_dataset.csv`: The input dataset
- `requirements_finalproject.txt`: File containing all the correct packages to download if using a local Jupyter notebook for reproducibility

3. Requirements and Dependencies

**Platform.** The notebook is designed for Google Colab. The notebook can also run in a local Jupyter environment with Python 3.10 or later.
**Packages** Packages needed if using a local Jupyter notebook are listed in `requirements_finalproject.txt`. This can be downloaded and installed.
**Jupyter notebook specific** If using a local Jupyter notebook, one line needs to be replaced in the file upload cell (Section 1A). The collab upload prompt (uploaded = files.upload()) is replaced with (filename = "Sleep_health_and_lifestyle_dataset.csv"). Make sure to put the data CSV file in the same path as the Jupyter notebook. 
**Reproducibility** A fixed random seed (`RANDOM_STATE = 42`) is used for the train/test split, the cross-validation folds, and every model, so repeated runs give the same result. 


3. Execution Instructions
  
1. Open Github repo (https://github.com/sudiksharamakrishnanhse-lab/ProgrammingforHDS_FinalProject/tree/main) and download `Sleep_health_and_lifestyle_dataset.csv`, `requirements_finalproject.txt`, and `FinalProject_ProgrammingforHDS_SR.ipynb`
2. Open Google Colab and load the notebook with **`Sleep_health_and_lifestyle_dataset.csv`, then upload the notebook. 
3. Run all cells in order with **Runtime, then Run all** (or one at a time from top to bottom).
4. At Section 1A, the run pauses and a **Choose Files** button appears. The file `Sleep_health_and_lifestyle_dataset.csv` is selected, and the run continues after the upload completes.
5. The remaining sections run without further input. The whole notebook takes roughly 40 seconds to 1 minute to fully run.

4. Notebook Outline

- 0: Imports
- 1: Data import and validation
- 2: Data cleaning 
- 3: Descriptive statistics
- 4: Exploratory visualizations
- 5: Inferential statistics
- 6: Feature engineering and train/test split
- 7: Supervised machine learning models
- 8: Model evaluation and comparison
- 9: Interpretation of findings

5. Dataset Exploration

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


6. Project Planning & Notebook Outline

**Evaluation Metrics**
- Recall (sensitivity): In screening, a missed case costs more than a false alarm.
- F1-score: Balances recall against precision.
- ROC-AUC: Threshold-independent measure of separation.
- Precision, specificity, balanced accuracy, MCC, PR-AUC: Show how the model handles false alarms.
- Accuracy: Can mislead if classes are uneven.

**Models** Logistic Regression, Decision Tree, Random Forest, and Gradient Boosting, each trained and tuned in its own section of the notebook (Sections 7B to 7E), placed in a scikit-learn `Pipeline` and tuned with `GridSearchCV` (scored by F1) using cross-validation folds that keep identical rows together. The best model is selected by cross-validated F1 on the training data, keeping the test set as an independent final check.

7. Pipeline Enhancements
Five enhancements go beyond the required components.

1. Enhancement 1: File upload with file-type detection and input validation (Section 1A)
- **What was modified:** The data is imported through an upload prompt that detects the file type (CSV, TSV, TXT, Excel, JSON, or Parquet), rejects anything other than exactly one file, raises a clear error for unsupported file types, and keeps the real category 'None' from being read as a missing value.
- **Why it was implemented:** A hard-coded file path breaks when the notebook is moved or the file type changes, and pandas would otherwise turn the label 'None' (no sleep disorder) into a missing value.
- **How it improves the analytical workflow:** Anyone can rerun the notebook with their own copy of the data, bad input fails with a readable message instead of a traceback, and the negative class is not silently lost.


2. Enhancement 2: Modular functions and Markdown organization (Sections 2, 6A, 8A)
- **What was modified:** Repeated steps were refactored into reusable functions (clean_dataset, engineer_features, and get_extra_metrics, which adds specificity, balanced accuracy, MCC, and PR-AUC to the template's metrics), and every section has a Markdown heading, a short description, and an outline at the top of the notebook.
- **Why it was implemented:** Steps copied across several cells are hard to maintain and easy to apply inconsistently.
- **How it improves the analytical workflow:** The notebook is easier to read, review, and reuse, and the same cleaning and feature logic can be applied to new data with a single function call.


3. Enhancement 3: Feature engineering (Section 6A)
- **What was modified:** Five features are created from existing columns: pulse pressure, mean arterial pressure, a high-blood-pressure flag, a short-sleep flag, and a stress-sleep gap. They are added to the model inputs and flagged in the feature importance table.
- **Why it was implemented:** They combine columns into clinically meaningful measures that the models might not discover on their own.
- **How it improves the analytical workflow:** The models receive more informative inputs, and the importance table shows whether the new features are actually used.


4. Enhancement 4: Conditional duplicate-aware splitting (Section 6B)
- **What was modified:** The train/test split first counts duplicate rows. If any exist, rows with identical predictor values are grouped and kept together in both the train/test split and the cross-validation folds. If none exist, the template's standard stratified split is used.
- **Why it was implemented:** 265 of the 374 rows repeat another row's predictor values, so a plain random split can put copies of the same row in both the training and test sets.
- **How it improves the analytical workflow:** Test scores are not inflated by the model having already seen near-identical rows. 


5. Enhancement 5: Cross-validated model comparison with fold-level variability (Section 8C)
- **What was modified:** A new comparison table shows the F1-score of every model on each cross-validation fold, together with each model's mean, standard deviation, range, and the number of folds in which it scored highest. 
- **Why it was implemented:** The models' average scores differ by less than 0.005, and an average alone cannot show whether such a small difference is real or only noise from a small dataset.
- **How it improves the analytical workflow:** The comparison shows directly whether any model is consistently better or whether the models are tied within normal fold-to-fold variation, which makes the model-selection decision and the written conclusion evidence-based.


8. Key Findings & Interpretation
**BMI and the outcome.** BMI was the most informative varaible where  the disorder rate is 7% among people with Normal BMI (16 of 216), 87% among Overweight people (129 of 148), and 100% among Obese people (10 of 10).
**Phi-K associations.** Systolic pressure (0.91), diastolic pressure (0.90), sleep duration (0.87), and age (0.82) show the strongest associations with the outcome; BMI category (0.54) is moderate and gender (0.42) is the weakest.

**Model Performance**
The four models are close: their cross-validated F1 scores differ by at most 0.020, while the fold-to-fold standard deviations are 0.044 to 0.081. Logistic Regression, Random Forest, and Gradient Boosting made identical predictions for all 91 test people, and the Decision Tree differed on 4. The fold-level comparison (Enhancement 4) shows no consistent leader: the best score changes from fold to fold, and each model's F1 ranges over 0.12 to 0.25 across folds. 

**Important features.** In the selected Random Forest, BMI category is the largest single contributor (about 30% of importance), and the blood pressure variables together contribute about 40%. Gender contributes almost nothing (about 0.6%), and quality of sleep and stress contribute modest shares (about 4% and 2%).

**Conclusion.** Routine variables, mainly BMI category, and blood pressure identify the presence of a sleep disorder in this dataset with high recall and good precision, and simple models perform about as well as complex ones. 


9. Limitations
- The sample is small, and the test set has 91 rows built from repeated profiles, so test metrics are uncertain. The training and test sets also differ in the share of disorder cases (36.0% vs. 58.2%).
- The dataset appears to be non-clinical and possibly synthetic as associations are unusually strong and many profiles are duplicated.
- Sleep quality and stress level are self-reported and are subjective ratings. 
- Insomnia and sleep apnea are merged into one class, although they differ in causes and typical risk factors.
- The results describe association and prediction, not causation.

