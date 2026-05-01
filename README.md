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
*  Metric : Test Accuracy , Weighted F1 , Recall (Class 3 - Pathological)
*  Score:  93.19%  ,  0.93 ,  86%
* Show one 

### Conclusions

* Random Forest is highly effective for medical tabular data where class boundaries are non-linear. The most critical features for detecting fetal pathology are abnormal short-term variability and prolonged decelerations.

### Future Work

* Implement SMOTE (Synthetic Minority Over-sampling Technique) to better balance the Suspect and Pathological classes.
* Explore XGBoost or LightGBM to see if gradient boosting provides a lift in F1-score over the Random Forest baseline.

## How to reproduce results

* Download fetal_health.csv from Kaggle.
* Run the provided Python script to perform scaling, training, and evaluation.
* Ensure your environment matches the Software Setup listed below.

### Overview of files in repository

* Files:
  * fetal_health.csv: The raw dataset.
  * analysis_and_model.py: The complete script for cleaning, visualizing, and training.
  * feature_summary.csv: A generated table of data statistics.
  * fetal_health_predictions.csv: The final output of the model on the test set.
  * histograms_features_vs_class.png: Visual exploration of the features.
    

### Software Setup
* Python 3.8+
* Packages: pandas, numpy, matplotlib, seaborn, scikit-learn.
* Install via pip: pip install pandas numpy matplotlib seaborn scikit-learn


## Citations

* Ayres de Campos et al. (2000) SisPorto 2.0: A Program for Automated Analysis of Cardiotocograms.
* Kaggle Dataset: Andrew MVD, "Fetal Health Classification".






