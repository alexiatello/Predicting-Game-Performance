# Predicting Student Performance from Game Play (Kaggle Project)

## Summary: 
This repository uses Machine Learning principles for data from a Game Play Performance Kaggle challenge, focusing on feature engineering principles for features from game play sessions. https://www.kaggle.com/competitions/predict-student-performance-from-game-play/data

## Overview

This repository contains a machine learning approach to the Kaggle competition *"Predict Student Performance from Game Play"*. The goal is to predict whether a student will answer a question correctly based on time-series interaction logs from an educational game environment. Each record represents user activity such as navigation events, hover behavior, room coordinates, and time spent on actions. In this project, the problem is approached as a **classification task at the session level**, where feature engineering summarizes student behavior across the gameplay sessions.
Several models including Logistic Regression, Decision Tree, and Random Forest are compared and used to evaluate the predictive performance. Logistic Regression was found to be the best model, sitting at a little over 80%.

---

## Summary of Work

## Data

- `train.csv`: Time-series log of student interactions 
- `train_labels.csv`: Target labels (correct/incorrect answers) 
- `test.csv`: Test set for prediction

### Structure
- Each row = one user interaction event
- Key columns:
  - session_id
  - event_name
  - elapsed_time
  - hover_duration
  - room coordinates
  - level information

### Size
- 
- 

---

## Preprocessing & Feature Engineering

The raw time-series data was transformed into session-level features using aggregation:

- Maximum elapsed time per session
- Mean hover duration
- Total number of actions
- Event diversity (unique event types per session)
- Most frequent event per session
- Maximum level reached
- Room exploration diversity
- Interaction speed (actions per second)

Missing values were handled by:
- Filling NaN hover values with 0

---

## Data Visualization

<img width="820" height="561" alt="image" src="https://github.com/user-attachments/assets/a902e56f-5a4e-462d-ada7-4de05c6d8be5" />

<img width="917" height="568" alt="image" src="https://github.com/user-attachments/assets/b4d83ebc-14e2-48cc-a06d-2b97dcd3de29" />

<img width="861" height="522" alt="image" src="https://github.com/user-attachments/assets/29c22344-4ce0-488f-8a9e-cf89615e10ba" />

<img width="872" height="181" alt="image" src="https://github.com/user-attachments/assets/9fc5281b-588a-44c9-8ca0-427c6f4d25ef" />

<img width="791" height="542" alt="image" src="https://github.com/user-attachments/assets/2894c2d6-1e06-4a3a-9f75-8146a74460ac" />


Exploratory analysis included:
- Event frequency distributions
- Relationship between time spent and number of actions
- Histograms of engineered session-level features

Observations:
- Certain events dominated user interaction
- Higher engagement sessions tend to have higher action counts

---

## Problem Formulation

### Input
Session-level feature vectors derived from raw gameplay logs

### Output
Binary classification:
- 1 = correct answer
- 0 = incorrect answer

---

## Models

The following models were implemented:

- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier

### Parameters
- Default sklearn settings used for baseline models
- Train-test split: 80/20
- Initial issue was generating random data, so coded random state to ensure it pulled from the specific training set.

---

## Performance Comparison

| Model               | Accuracy |
|--------------------|----------|
| Logistic Regression | ~0.83    |
| Decision Tree       | ~0.66    |
| Random Forest       | ~0.77–0.94  (depending on size of sample)|

Logistic Regression generally performed best in stability.

---

## Conclusions

- Aggregated session-level features are effective for prediction
- Ensemble methods outperform single decision trees
- Simple models already achieve strong baseline performance

---

## Future Work

- Hyperparameter tuning (GridSearchCV)
- Sequence-based deep learning models (LSTM/GRU)
- More advanced temporal feature extraction
- Handling class imbalance more explicitly

---

## How to Reproduce Results

### Requirements
- Python 3.8+
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

### Steps
1. Load `train.csv`
2. Run feature engineering section in `data_visual.ipynb`
3. Train models using generated `session_features`
4. Evaluate using train/test split

---

## File Structure

- `data_visual.ipynb` → Full pipeline: preprocessing, feature engineering, modeling
- `.gitignore` → Excludes datasets and large files
- `train.csv` (ignored) → Raw Kaggle dataset (not included in repo)

---

## Citations

Kaggle Competition: Predict Student Performance from Game Play  
https://www.kaggle.com/competitions/predict-student-performance-from-game-play
