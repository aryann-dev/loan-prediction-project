# Loan Prediction Project

A machine learning model that predicts whether a loan application will be approved, based on the
applicant's personal, financial and credit details. Built with a Random Forest classifier, it reaches
**76.4% accuracy** on a held-out test set.

## Overview

Lenders need to decide quickly and consistently whether to approve a loan. This project walks through a
complete, beginner-friendly classification workflow in a single Jupyter notebook:

1. Load and explore the data
2. Handle missing values
3. Visualise approval patterns
4. Encode categorical features
5. Train and evaluate a Random Forest model

## Dataset

The notebook expects a `train.csv` file (not included in this repository) with **614 loan applications**
and 13 columns:

| Column | Description |
|---|---|
| `Loan_ID` | Unique application ID (dropped before training) |
| `Gender`, `Married`, `Dependents`, `Education`, `Self_Employed` | Applicant profile |
| `ApplicantIncome`, `CoapplicantIncome` | Monthly income of the applicant and co-applicant |
| `LoanAmount`, `Loan_Amount_Term` | Requested amount and term |
| `Credit_History` | Whether the applicant's credit history meets guidelines |
| `Property_Area` | Urban, semi-urban or rural |
| `Loan_Status` | **Target:** approved (`Y`) or not approved (`N`) |

## Methodology

**Data cleaning**
- Categorical columns with missing values (`Gender`, `Married`, `Dependents`, `Self_Employed`,
  `Loan_Amount_Term`, `Credit_History`) are filled with the most frequent value (mode).
- `LoanAmount` is filled with the mean.

**Exploratory analysis**
- Count of approved vs. rejected applications.
- Approval rate by education level.

**Feature engineering**
- Categorical columns are converted to numbers with `LabelEncoder`.
- `Loan_ID` is removed; all remaining columns are used as features.

**Model**
- 80/20 train/test split (`random_state=42`).
- `RandomForestClassifier` with default settings.

## Results

| Model | Test accuracy |
|---|---|
| Random Forest | **76.4%** |

The test set contains 123 applications. Because the Random Forest is not seeded, accuracy can vary
slightly between runs.

## Tech Stack

Python, pandas, NumPy, scikit-learn, Matplotlib, Seaborn, Jupyter Notebook

## How to Run

```bash
git clone https://github.com/aryann-dev/loan-prediction-project.git
cd loan-prediction-project
pip install pandas numpy scikit-learn matplotlib seaborn notebook
```

Place `train.csv` in the project folder, then open and run the notebook:

```bash
jupyter notebook Untitled.ipynb
```

## Future Improvements

- Compare against other models (Logistic Regression, Gradient Boosting, XGBoost).
- Tune hyperparameters with cross-validation.
- Report precision, recall, F1-score and a confusion matrix in addition to accuracy.
- Add feature importance analysis to explain which factors drive approval.
- Use one-hot encoding for nominal features such as `Property_Area`.
