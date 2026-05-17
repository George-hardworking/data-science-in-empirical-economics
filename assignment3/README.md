# Assignment 3: Predicting Firm Default Risk with Supervised Learning

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Topic | Firm Default Risk Prediction |
| Data | Firm financial panel data with default indicators |
| Framework | Supervised Learning, Binary Classification, Credit Risk Modeling |

## Overview

This assignment builds supervised learning models to predict firm default using financial covariates. It covers the complete empirical workflow: problem framing (binary classification), data preparation (dummy encoding, train-test splitting), baseline logistic regression with economic interpretation, Random Forest ensemble methods with hyperparameter tuning, and a discussion of economic implications for credit policy.

The analysis emphasizes class-imbalance-aware evaluation metrics (ROC-AUC, precision-recall for the default class) and economic interpretation of model coefficients and feature importances.

## Tasks

1. **Problem Setup** (Conceptual): Frame default prediction as binary classification; discuss why false negatives matter more than false positives; explain why "always predict no default" is insufficient at 5% default rate.
2. **Data Preparation**: Load firm panel data, apply one-hot encoding to categorical variables (`sector`, `region`), and perform 70/30 train-test split.
3. **Logistic Regression Baseline**: Estimate binary logistic regression with L-BFGS solver; evaluate accuracy, precision, recall, F1, and ROC-AUC on test set; provide economic interpretation of leverage and previous default coefficients.
4. **Random Forest**: Fit Random Forest (200 estimators); compare test-set performance with logistic regression; visualize and interpret feature importances.
5. **Hyperparameter Tuning**: Grid search over `max_depth` and `min_samples_leaf` with 5-fold stratified cross-validation (ROC-AUC scoring); evaluate tuned model on test set.
6. **Economic Interpretation**: Discuss implications of a 10% predicted-default-probability cutoff for loan approval; analyze effects on young vs. old firms and sectoral credit allocation; address risk management and fairness concerns.

## Repository Structure

```text
assignment3/
├── raw/
│   └── firms_default.csv              # Firm financial panel with default labels
├── scripts/
│   └── assignment3_kaibiao.ipynb     # Main analysis notebook
├── outputs/                          # Generated outputs (tables, figures)
├── docs/
│   └── HW3_IPEN 5810_2026S.pdf      # Assignment instructions
└── README.md
```

## Main Analysis File

```text
scripts/assignment3_kaibiao.ipynb
```

The notebook is structured as:

1. Problem setup and conceptual framing
2. Data loading, descriptive statistics, dummy encoding, train-test split
3. Logistic regression: estimation, test-set evaluation, coefficient interpretation
4. Random Forest: estimation, test-set comparison with logistic regression
5. Feature importance analysis (MDI)
6. Hyperparameter grid search with 5-fold stratified CV
7. Economic interpretation and policy implications

## Environment

Python 3.10+ is recommended.

Key packages include:

- `pandas`, `numpy`
- `scikit-learn` (LogisticRegression, RandomForestClassifier, GridSearchCV, metrics)
- `matplotlib`

## How to Run

From the repository root:

```bash
jupyter nbconvert \
  --to notebook \
  --execute assignment3/scripts/assignment3_kaibiao.ipynb \
  --output assignment3_kaibiao_executed.ipynb \
  --output-dir assignment3/outputs \
  --ExecutePreprocessor.kernel_name=5020_env
```

Or run interactively in Jupyter using the `5020_env` kernel.

## Outputs

Running the notebook generates:

- Descriptive statistics of the firm panel
- Logistic regression coefficients and test-set performance metrics
- Random Forest test-set metrics and comparison table
- Feature importance bar chart
- Cross-validation results and tuned model comparison
- Economic interpretation discussion

## Notes on Reproducibility

- Random state is set to `123` for train-test split, Random Forest, and cross-validation.
- Train-test split is 70/30 with default random shuffle.
- Metrics for the default class (`pos_label=1`) use `zero_division=0`.
- The notebook should be run from a clean kernel for final reproduction.

## License

This assignment is for course project submission and academic use.
