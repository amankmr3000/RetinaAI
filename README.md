# Student Dropout Risk Prediction

This project was built for the Retina AI Hackathon 2026.

The goal was to predict student dropout risk using academic records, attendance history, and counsellor notes. The idea is to identify students who might be struggling before they actually drop out so that institutions can take action early.

---

## Problem Statement

Many students show warning signs before leaving college, but these signs are often spread across multiple sources such as grades, attendance records, and counsellor interactions.

The objective was to combine these different sources of information and predict the dropout risk level of each student.

---

## Dataset

The dataset consisted of three different modalities:

### Academic Data
- CGPA
- Backlogs
- Credits
- Student information

### Attendance Data
- More than 1 million attendance records
- Daily attendance logs

### Counsellor Notes
- 15,000 text notes
- Feedback and observations about students

Dataset size:

| Data | Count |
|--------|--------|
| Train Students | 12,000 |
| Test Students | 3,000 |
| Attendance Records | 1,048,575 |
| Counsellor Notes | 15,000 |

---

## What I Did

### Attendance Features

The raw attendance data contained more than 1 million records, so I first aggregated it at the student level.

Some features created:

- Mean attendance
- Attendance trend
- Attendance variability
- Consecutive absences
- Attendance recovery rate

### Academic Features

I created features that capture student performance over time.

Examples:

- CGPA trend
- Backlog trend
- Grade consistency
- Credit performance

### Counsellor Notes

For the text data, I used TF-IDF vectorization and extracted useful signals from the notes.

Examples:

- Risk keywords
- Topic indicators
- Sentiment-related features

---

## Models Tried

During experimentation I tested multiple approaches:

- CatBoost
- XGBoost
- Logistic Regression
- Ensemble Models

CatBoost performed best on structured data while Logistic Regression worked well with TF-IDF features.

---

## Experiment Journey

| Experiment | Macro F1 |
|------------|-----------|
| Organizer Benchmark | 0.6339 |
| CatBoost Baseline | 0.7100 |
| CatBoost + Attendance Features | 0.7140 |
| CatBoost + Attendance + NLP | 0.7167 |
| Ensemble + Tuning | 0.7205 |
| Final Model | **0.7214** |

Final improvement over benchmark:

**0.6339 → 0.7214 (+13.8%)**

---

## Final Solution

The final submission used a weighted ensemble:

- CatBoost (55%)
- Logistic Regression + TF-IDF (35%)
- XGBoost (10%)

This combination gave the most stable cross-validation performance.

---

## Results

**Final Macro F1 Score: 0.7214**

Some things that helped improve performance:

- Attendance trend features
- NLP features from counsellor notes
- Ensemble weighting
- Threshold tuning

---

## Challenges

Some challenges I faced during the project:

- Processing 1M+ attendance records
- Noisy counsellor notes
- Class imbalance
- Feature selection

A lot of engineered features looked promising but did not actually improve cross-validation scores.

---

## Future Improvements

If I continue working on this project, I would like to:

- Use DistilBERT instead of TF-IDF
- Add SHAP explainability
- Build a Streamlit dashboard
- Deploy the model for real-time predictions


## Author

Aman Kumar

ABES Engineering College

Retina AI Hackathon 2026
