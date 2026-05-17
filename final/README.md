# Final Project: Disclosure Timing as a Public Risk Signal in China's A-Share Market

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Topic | Disclosure Timing, Market Risk, and Economic Value |
| Data | AkShare stock-market data, financial panel, disclosure schedules, earnings forecasts |
| Framework | Supervised Learning, Event Studies, Portfolio Analysis |

## Project Overview

This research project investigates whether publicly observable annual-report disclosure schedules contain incremental information about bad news and announcement-window downside risk in China's A-share market, beyond standard financial fundamentals. The paper reframes an earlier ST-prediction exercise into an economics question about strategic disclosure and market information processing.

The analysis uses free AkShare data, tests whether disclosure-timing behavior is a real-time, publicly observable risk signal with out-of-sample predictive value and economic value, and presents results through a complete academic paper with LaTeX report.

## Repository Structure

```text
final/
├── improved_version_disclosure_timing/    # Final submission version
│   ├── raw/
│   │   └── raw_financial_panel.csv        # Original financial panel data
│   ├── scripts/
│   │   └── final_submit_version.ipynb     # Main research notebook
│   ├── output/                            # All generated outputs
│   │   ├── raw/                           # AkShare cached data (disclosure schedules, earnings forecasts, prices)
│   │   ├── intermediate/                  # Cleaned/merged analysis panels
│   │   ├── figures/                       # Generated figures
│   │   ├── tables/                        # Result tables (CSV)
│   │   ├── models/                        # Saved trained models
│   │   └── docs/                          # Auto-generated documentation
│   ├── latex_report/                      # LaTeX source for research paper
│   │   ├── report.tex                     # Main LaTeX document
│   │   ├── compile.sh                     # Reproducible build script
│   │   ├── output/                        # Compiled PDF
│   │   └── build/                         # Temporary build files
│   └── docs/
│       └── Project Guidelines-IPEN 5810-2026S.pdf
├── initial_version_st_prediction/         # Initial exploration version
│   ├── raw/
│   │   └── raw_financial_panel.csv
│   ├── scripts/
│   │   └── final_initial_version.ipynb    # Initial ST prediction notebook
│   ├── output/                            # Generated outputs
│   │   ├── figures/
│   │   ├── tables/
│   │   └── models/
│   └── docs/
│       └── README.md                      # Project requirements document
└── README.md
```

## Main Analysis File

```text
improved_version_disclosure_timing/scripts/final_submit_version.ipynb
```

The notebook is structured as:

1. Environment setup, path configuration, and reproducibility settings
2. Helper functions (stock code parsing, numeric cleaning, AkShare retry, evaluation metrics)
3. Fetch and cache disclosure schedules and earnings forecasts from AkShare (2019–2023)
4. Market price data fetching and event-study return calculations
5. Merge and construct analysis panel with disclosure timing features
6. LightGBM prediction models with feature engineering
7. Event-study analysis of abnormal returns around disclosure dates
8. Economic value assessment via portfolio analysis
9. Robustness checks and alternative specifications

## How to Run

### Notebook

From the repository root:

```bash
jupyter nbconvert \
  --to notebook \
  --execute final/improved_version_disclosure_timing/scripts/final_submit_version.ipynb \
  --output final_submit_version_executed.ipynb \
  --output-dir final/improved_version_disclosure_timing/output \
  --ExecutePreprocessor.timeout=3600 \
  --ExecutePreprocessor.kernel_name=5020_env
```

Or run interactively in Jupyter using the `5020_env` kernel.

### LaTeX Report

After running the notebook (to generate figures), compile the report:

```bash
conda run --no-capture-output -n 5020_env bash final/improved_version_disclosure_timing/latex_report/compile.sh
```

The compiled PDF will be at `final/improved_version_disclosure_timing/latex_report/output/report.pdf`.

## Outputs

Running the notebook regenerates the following under `output/`:

- **Tables**: Sample statistics, disclosure timing regressions, bad-news prediction metrics, incremental AUC (bootstrap), LightGBM feature importance, event-study CAR metrics, economic value results, robustness checks
- **Figures**: Disclosure timing distributions, ROC curves, feature importance plots, event-study plots, portfolio performance charts
- **Models**: Trained LightGBM models
- **Intermediate data**: Cleaned panels for further analysis

## Notes on Reproducibility

- Random seed is set to `42` in the first code cell.
- AkShare data fetching includes retry logic with exponential backoff.
- All intermediate files are cached in `output/raw/` to minimize API calls.
- The LaTeX report imports figures from `output/figures/`, so the notebook should be run before compiling the report.
- The notebook uses paths relative to the project root for all file I/O.

## License

This project is for course project submission and academic use.
