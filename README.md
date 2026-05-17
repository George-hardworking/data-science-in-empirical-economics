# Data Science in Empirical Economics

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Date | May 2026 |
| Topics | Text Mining, Geospatial Analysis, Default Risk Prediction, Disclosure Timing |
| Framework | Supervised Learning, Natural Language Processing, Geospatial Data Science, Event Studies |

## Project Overview

This repository contains the coursework for **IPEN 5810 — Data Science in Empirical Economics**. It includes four assignments and a final research project, covering a wide range of topics at the intersection of data science and empirical economics:

- **Assignment 1 — Text Mining & Topic Modeling**: Preprocesses MPC (Monetary Policy Committee) minutes and applies TF-IDF, LDA topic modeling, and NPMI coherence analysis to uncover latent themes in central bank communications.
- **Assignment 2 — Geospatial Analysis with CDL Data**: Reads and analyzes USDA Cropland Data Layer (CDL) raster files for California (2022–2023), including binary crop mapping, land-use ranking, and crop rotation analysis.
- **Assignment 3 — Default Risk Prediction**: Builds supervised learning models (Logistic Regression, Random Forest) to predict firm default using financial covariates, with a focus on class imbalance and economic interpretation.
- **Final Project — Disclosure Timing as a Public Risk Signal**: An empirical research paper investigating whether publicly observable annual-report disclosure schedules contain incremental information about bad news and downside risk in China's A-share market.

## Repository Structure

```text
.
├── assignment1/                            # Text Mining & Topic Modeling
│   ├── raw/
│   ├── scripts/
│   │   └── assignment1_kaibiao.ipynb
│   ├── output/
│   └── docs/
├── assignment2/                            # Geospatial Analysis
│   ├── raw/
│   ├── scripts/
│   │   └── assignment2_kaibiao.ipynb
│   ├── output/
│   └── docs/
├── assignment3/                            # Default Risk Prediction
│   ├── raw/
│   ├── scripts/
│   │   └── assignment3_kaibiao.ipynb
│   ├── outputs/
│   └── docs/
├── final/                                  # Final Research Project
│   ├── improved_version_disclosure_timing/ # Final submission version
│   │   ├── raw/
│   │   ├── scripts/
│   │   │   └── final_submit_version.ipynb
│   │   ├── output/
│   │   ├── latex_report/
│   │   └── docs/
│   ├── initial_version_st_prediction/      # Initial exploration version
│   │   ├── raw/
│   │   ├── scripts/
│   │   ├── output/
│   │   └── docs/
│   └── README.md
├── requirements.txt
└── README.md
```

## Assignments

### Assignment 1: Text Mining & Topic Modeling

Analyzes MPC meeting minutes using NLP techniques. Covers text preprocessing (tokenization, stemming, lemmatization), document frequency ranking, TF-IDF feature extraction, and LDA topic modeling with 30 topics. Includes NPMI-based coherence evaluation and manual interpretation of latent themes.

**Notebook:** `assignment1/scripts/assignment1_kaibiao.ipynb`

### Assignment 2: Geospatial Analysis

Processes 30m-resolution CDL raster data for California (2022–2023). Implements block-based raster I/O for memory efficiency, binary crop mapping for almonds and grapes, top-10 land-use area ranking, and pixel-level crop rotation transition analysis using Rasterio and GeoPandas.

**Notebook:** `assignment2/scripts/assignment2_kaibiao.ipynb`

### Assignment 3: Default Risk Prediction

Builds a binary classification pipeline for firm default prediction. Covers problem framing (classification vs. regression), cost-sensitive reasoning, logistic regression baseline with economic interpretation, and Random Forest comparison. Emphasizes ROC-AUC evaluation and class-imbalance-aware metrics.

**Notebook:** `assignment3/scripts/assignment3_kaibiao.ipynb`

### Final Project: Disclosure Timing as a Public Risk Signal

An empirical research paper testing whether annual-report disclosure schedules contain incremental information about bad news and market risk. Uses AkShare data, LightGBM models, event-study methodology, and economic value assessment. Includes a full LaTeX report.

**Notebook:** `final/improved_version_disclosure_timing/scripts/final_submit_version.ipynb`

## Environment

Python 3.10+ is recommended.

Key packages include:

- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `scikit-learn`
- `nltk`
- `rasterio`, `geopandas`
- `lightgbm`
- `statsmodels`
- `akshare`

## How to Run

Each notebook uses paths relative to its own location. Recommended commands from the repository root:

```bash
# Assignment 1
jupyter nbconvert --to notebook --execute assignment1/scripts/assignment1_kaibiao.ipynb --output-dir assignment1/output

# Assignment 2
jupyter nbconvert --to notebook --execute assignment2/scripts/assignment2_kaibiao.ipynb --output-dir assignment2/output

# Assignment 3
jupyter nbconvert --to notebook --execute assignment3/scripts/assignment3_kaibiao.ipynb --output-dir assignment3/outputs

# Final Project
jupyter nbconvert --to notebook --execute final/improved_version_disclosure_timing/scripts/final_submit_version.ipynb --output-dir final/improved_version_disclosure_timing/output
```

All notebooks should be run using the Conda environment `5020_env` for package compatibility.

## License

This repository is for course project submission and academic use.
