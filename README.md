# Vessel Deficiency Severity Prediction Model

## Overview
The maritime industry faces challenges in consistently assessing and predicting the severity of deficiencies found during vessel inspections. Diverging opinions among inspectors and the complexity of interpreting technical descriptions make this process difficult. This project aims to develop a systematic approach to derive consensus severity ratings from Subject Matter Expert (SME) annotations and predict severity using machine learning.

We employed a majority voting technique to ensure consensus in SME annotations and used machine learning techniques, including AutoML with FLAML, to predict severity efficiently.

## Methodology

### 1. Deriving Consensus Severity
- Used the **majority voting technique** to derive the final severity rating from SME annotations.
- Converted severity labels into numerical values:
  - **High** → `3`
  - **Medium** → `2`
  - **Low** → `1`
- This approach ensures the final decision reflects the predominant view while minimizing the impact of extreme ratings.

**Assumptions:**
- No null values in the dataset.
- All inspectors are considered equally reliable.

### 2. Predictive Model
#### Data Preparation
- Converted `InspectionDate` to Unix timestamps.
- Encoded categorical variables (e.g., `VesselGroup`).
- Used **BERT embeddings** to capture nuanced meanings in textual descriptions (`def_text`).
- Removed irrelevant columns (`VesselId`, `PscInspectionId`, `annotation_id`, `username`).

#### Model Selection
- Utilized **AutoML (FLAML)** to automate model selection, hyperparameter tuning, and training.
- Chose FLAML due to its:
  - **Low computational cost**
  - **Fast execution**
  - **Efficient search strategies** for optimal models

#### Validation
- Split the dataset into **80% training** and **20% validation**.
- Used **precision, recall, F1-score, and accuracy** to evaluate model performance.

## Requirements
To run this project, install the necessary Python libraries:
```bash
pip install numpy pandas scikit-learn transformers flaml
```

## Execution Steps
1. Load and preprocess the dataset.
2. Apply **majority voting** for consensus severity.
3. Convert text data using **BERT embeddings**.
4. Train models using **AutoML (FLAML)**.
5. Evaluate model performance using classification metrics.
6. Fine-tune hyperparameters for optimal results.

## References
- *Machine Learning for Maritime Safety Assessment*
- *BERT-Based NLP for Textual Data Interpretation in Inspections*
