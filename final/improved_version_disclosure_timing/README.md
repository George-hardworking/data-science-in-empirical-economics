# Improved Version: Disclosure Timing as a Public Risk Signal

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Version | Improved final submission |
| Topic | Disclosure Timing, Market Risk, and Economic Value |
| Data | AkShare disclosure schedules, earnings forecasts, stock returns, and financial panel data |
| Framework | Supervised Learning, Event Studies, Portfolio Analysis, Quasi-Causal Checks |

## Project Overview

This folder contains the improved final-project version. It reframes the initial ST-prediction exercise into an empirical economics question: whether publicly observable annual-report disclosure schedules contain incremental information about bad news and downside market risk in China's A-share market.

The project uses free AkShare data to construct disclosure-timing signals, merge them with firm fundamentals and earnings forecasts, evaluate out-of-sample bad-news prediction, estimate event-window abnormal returns, and assess practical economic value through a risk-screening portfolio exercise. The folder also includes a standalone LaTeX research report.

## Repository Structure

```text
improved_version_disclosure_timing/
├── raw/
│   └── raw_financial_panel.csv            # Original financial panel data
├── scripts/
│   └── final_submit_version.ipynb         # Main improved research notebook
├── output/
│   ├── raw/                               # Cached AkShare raw data
│   ├── intermediate/                      # Cleaned and merged analysis panels
│   ├── figures/                           # Generated figures
│   ├── tables/                            # Result tables
│   ├── models/                            # Saved trained models
│   └── docs/                              # Auto-generated output documentation
├── latex_report/
│   ├── report.tex                         # Main LaTeX paper
│   ├── compile.sh                         # Reproducible report build script
│   ├── output/                            # Compiled PDF report
│   └── build/                             # Temporary LaTeX build files
├── docs/
│   └── Project Guidelines-IPEN 5810-2026S.pdf
└── README.md
```

## Main Analysis File

```text
scripts/final_submit_version.ipynb
```

The notebook is structured as:

1. Environment setup, path configuration, and reproducibility settings
2. Helper functions for code parsing, numeric cleaning, AkShare retry logic, and evaluation
3. Disclosure schedule and earnings forecast data fetching from AkShare
4. Disclosure-timing feature construction and firm-year panel merging
5. Regression analysis of bad news and strategic disclosure timing
6. LightGBM prediction models and incremental information-value tests
7. SHAP and feature-importance interpretation of public risk signals
8. Event-study analysis around annual-report disclosure dates
9. Economic value assessment using real event-window stock returns
10. Robustness checks, placebo tests, and quasi-causal design diagnostics

## How to Run

From the repository root:

```bash
conda activate 5020_env

jupyter nbconvert \
  --to notebook \
  --execute final/improved_version_disclosure_timing/scripts/final_submit_version.ipynb \
  --output final_submit_version_executed.ipynb \
  --output-dir final/improved_version_disclosure_timing/output \
  --ExecutePreprocessor.timeout=3600 \
  --ExecutePreprocessor.kernel_name=5020_env
```

Or run the notebook interactively in Jupyter using the `5020_env` kernel.

## LaTeX Report

After running the notebook, compile the report from the repository root:

```bash
conda activate 5020_env

bash final/improved_version_disclosure_timing/latex_report/compile.sh
```

The compiled PDF will be written to:

```text
latex_report/output/report.pdf
```

## Outputs

Running the notebook regenerates the main outputs under `output/`:

- **Tables**: Sample statistics, disclosure-timing regressions, prediction metrics, incremental AUC bootstrap tests, event-study CAR metrics, economic value results, robustness checks, and software-version records
- **Figures**: Disclosure-timing descriptives, ROC comparisons, feature importance plots, SHAP summary plots, event-study CAR plots, economic value figures, placebo diagnostics, and causal-balance diagnostics
- **Models**: Trained bad-news prediction models saved in `output/models/bad_news_prediction_models.pkl`
- **Intermediate data**: Cleaned disclosure schedules, earnings forecast signals, event-study samples, and the merged analysis panel

## Notes on Reproducibility

- Random seed is set to `42` in the notebook.
- AkShare requests use retry logic and cached files under `output/raw/`.
- All generated tables, figures, intermediate files, and models are written under `output/`.
- The LaTeX report imports figures from `output/figures/`, so the notebook should be run before compiling the paper.
- Paths are defined relative to the repository root to keep the project reproducible across machines.

## License

This project is for course project submission and academic use.
