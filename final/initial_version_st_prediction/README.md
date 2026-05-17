# Initial Version: ST Risk Prediction in China's A-Share Market

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Version | Initial exploration |
| Topic | ST Risk Prediction and Financial Distress Signals |
| Data | AkShare financial panel data |
| Framework | Supervised Learning, Model Interpretation, Heterogeneity Analysis, DML |

## Project Overview

This folder contains the initial version of the final project. It studies whether firm-level financial indicators can predict future ST risk in China's A-share market and compares traditional econometric classification with machine-learning models.

The analysis builds a cleaned financial panel, estimates Logistic Regression, Random Forest, XGBoost, and LightGBM models, and uses SHAP interpretation, heterogeneity analysis, placebo checks, Double Machine Learning, and an economic-value simulation to connect prediction performance with empirical economics interpretation.

## Repository Structure

```text
initial_version_st_prediction/
├── raw/
│   └── raw_financial_panel.csv            # Original financial panel data
├── scripts/
│   └── final_initial_version.ipynb        # Main initial-version notebook
├── output/
│   ├── cleaned_financial_panel.csv        # Cleaned modeling dataset
│   ├── figures/                           # Generated figures
│   ├── tables/                            # Result tables
│   └── models/                            # Model output directory
├── docs/
│   └── Project Guidelines-IPEN 5810-2026S.pdf
└── README.md
```

## Main Analysis File

```text
scripts/final_initial_version.ipynb
```

The notebook is structured as:

1. Environment setup, path configuration, and package imports
2. Financial panel loading, cleaning, and feature preparation
3. Baseline Logistic Regression model for ST prediction
4. Random Forest, XGBoost, and LightGBM model comparisons
5. ROC, precision-recall, KS, and classification metric evaluation
6. Feature correlation analysis and model-importance visualization
7. SHAP summary, dependence, and local waterfall interpretation
8. Heterogeneity analysis by firm size and information asymmetry
9. Placebo testing and Double Machine Learning checks
10. Economic-value simulation based on risk screening

## How to Run

From the repository root:

```bash
conda activate 5020_env

jupyter nbconvert \
  --to notebook \
  --execute final/initial_version_st_prediction/scripts/final_initial_version.ipynb \
  --output final_initial_version_executed.ipynb \
  --output-dir final/initial_version_st_prediction/output \
  --ExecutePreprocessor.timeout=3600 \
  --ExecutePreprocessor.kernel_name=5020_env
```

Or run the notebook interactively in Jupyter using the `5020_env` kernel.

## Outputs

Running the notebook regenerates the following under `output/`:

- **Cleaned data**: `cleaned_financial_panel.csv`
- **Tables**: Baseline model metrics, full model-comparison metrics, heterogeneity analysis, and economic-value simulation results
- **Figures**: ROC and precision-recall curves, feature correlation heatmap, XGBoost gain importance, SHAP summary and dependence plots, DML causal-effect plot, placebo distribution, heterogeneity AUC comparison, and economic-value portfolio plot
- **Models**: Reserved output directory for saved model artifacts

## Main Findings

- Logistic Regression already captures the dominant linear ST-risk component, with test AUC around 0.960.
- Tree-based machine-learning models provide only modest incremental AUC gains, but they are useful for identifying nonlinear threshold effects through SHAP and dependence plots.
- Heterogeneity analysis suggests that predictive performance differs across firm-size groups, while the marginal gain from machine learning over Logistic Regression is limited.
- The DML exercise highlights the distinction between predictive importance and causal interpretation: highly predictive financial indicators may reflect symptoms of distress rather than root causes.
- The economic-value simulation translates model scores into a risk-screening exercise that avoids the highest-risk firms.

## Notes on Reproducibility

- The analysis uses the Conda environment `5020_env`.
- All file paths are organized within this folder and its `output/` directory.
- The notebook writes figures and tables directly to `output/figures/` and `output/tables/`.
- The initial version is preserved as an exploratory benchmark; the improved final submission is stored separately under `final/improved_version_disclosure_timing/`.

## License

This project is for course project submission and academic use.
