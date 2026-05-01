![](UTA-DataScience-Logo.png)

# Fetal Health Classification Project

* **Predicting Fetal Health via Cardiotocogram Exam Analysis** : This repositiory holds an attempt to classify fetal health into three categories (Normal, Suspect, Pathological) using features extracted from cardiotocogram exams found in fetal_healh.csv.

## Overview

* This section could contain a short paragraph which include the following:
  * **Definition of the tasks / challenge** : The task is to use 21 features extracted from fetal heart rate (FHR) and uterine contraction (UC) signals to predict a three-class target: Normal (1), Suspect (2), or Pathological (3).
  * **Approach** : This project formulates the problem as a multi-class classification task. I employed a Random Forest Classifier to handle the inherent class imbalance and non-linear relationships between physiological features. Data preparation included standard scaling and stratified splitting to ensure the model was evaluated on representative samples of the minority (Pathological) class.
  * **Summary of the performance achieved** : The best model achieved an Accuracy of 93.19% and a Weighted F1-Score of 0.93 on the hold-out test set. Specifically, the model demonstrated high reliability in identifying "Normal" cases (98% recall) while maintaining strong performance on the critical "Pathological" class (86% recall).

## Summary of Workdone

### Data

* Data:
  * Type: CSV file containing 21 numerical features (e.g., accelerations, fetal movement, uterine contractions) and 1 categorical target.
  * Size: 2,126 total records.
  * Instances (Train, Test, Validation Split):
          * Train: 1,275 instances (60%)
          * Validation: 425 instances (20%)
          * Test: 426 instances (20%)
#### Preprocessing / Clean up

* Missing Values: None detected; no imputation required.
* Scaling: Applied StandardScaler to all 21 features to ensure features like baseline value (range 100-160) didn't overshadow features like accelerations (range 0.0-0.02).
* Stratification: Used stratified sampling during the split to manage class imbalance (77% Normal vs 8% Pathological).

#### Data Visualization

* Histograms: Visualized feature distributions across classes. For example, abnormal_short_term_variability showed a clear shift toward higher values for Pathological cases.
* Feature Importance: A bar chart of Random Forest importance revealed that variability metrics and prolonged decelerations are the strongest predictors of fetal distress.


### Problem Formulation

* Define:
  * Input / Output : 21 physiological features as input; 3-class health status as output.
  * Models
    * Random Forest Classifier was selected because its robustness to outliers and ability to provide feature importance rankings.
  * Loss, Optimizer, other Hyperparameters :
                 * Hyperparameters : Default Scikit-Learn parameters with n_estimators=100 and random_state=42.

### Training

* Describe the training:
  * How you trained: Trained using Scikit-Learn on a local CPU (standard Python environment).
  * How did training take : Training was nearly instantaneous < 2 seconds due to the small dataset size.
  * How did you decide to stop training : Random Forest is an ensemble of trees; training stops once all 100 trees are fully grown.

### Performance Comparison

* Metrics: Accuracy, Precision, Recall, and Weighted F1-Score.
* Show/compare :
*  Metric,Score
Test Accuracy,93.19%
Weighted F1,0.93
Recall (Class 3 - Pathological),86%
* Show one (or few) visualization(s) of results, for example ROC curves.

### Conclusions

* State any conclusions you can infer from your work. Example: LSTM work better than GRU.

### Future Work

* What would be the next thing that you would try.
* What are some other studies that can be done starting from here.

## How to reproduce results

* In this section, provide instructions at least one of the following:
   * Reproduce your results fully, including training.
   * Apply this package to other data. For example, how to use the model you trained.
   * Use this package to perform their own study.
* Also describe what resources to use for this package, if appropirate. For example, point them to Collab and TPUs.

### Overview of files in repository

* Describe the directory structure, if any.
* List all relavent files and describe their role in the package.
* An example:
  * utils.py: various functions that are used in cleaning and visualizing data.
  * preprocess.ipynb: Takes input data in CSV and writes out data frame after cleanup.
  * visualization.ipynb: Creates various visualizations of the data.
  * models.py: Contains functions that build the various models.
  * training-model-1.ipynb: Trains the first model and saves model during training.
  * training-model-2.ipynb: Trains the second model and saves model during training.
  * training-model-3.ipynb: Trains the third model and saves model during training.
  * performance.ipynb: loads multiple trained models and compares results.
  * inference.ipynb: loads a trained model and applies it to test data to create kaggle submission.

* Note that all of these notebooks should contain enough text for someone to understand what is happening.

### Software Setup
* List all of the required packages.
* If not standard, provide or point to instruction for installing the packages.
* Describe how to install your package.

### Data

* Point to where they can download the data.
* Lead them through preprocessing steps, if necessary.

### Training

* Describe how to train the model

#### Performance Evaluation

* Describe how to run the performance evaluation.


## Citations

* Provide any references.







