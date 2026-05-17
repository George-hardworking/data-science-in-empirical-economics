# Disclosure Timing Project Outputs

## Research Question
Do publicly observable annual-report disclosure schedules contain incremental information about bad news and announcement-window downside risk beyond standard financial fundamentals?

## Data
- Annual-report disclosure schedules: AkShare `stock_yysj_em`, fiscal years 2019-2023.
- Earnings forecasts: AkShare `stock_yjyg_em`.
- Firm fundamentals: existing AkShare financial panel in `final/improved_version_disclosure_timing/raw/raw_financial_panel.csv`.
- Event-study stock returns: AkShare `stock_zh_a_daily`, cached by stock code. Short-window event returns use unadjusted close prices for API stability.
- Market benchmark: AkShare `stock_zh_index_daily`, CSI 300 (`sh000300`).

## Main Sample
- Firm-year observations: 10,455.
- Fiscal years: 2019-2023.
- Realized bad-news rate: 22.77%.
- Valid event-study windows: 240.

## Core Outputs
- `tables/table_03_disclosure_timing_regressions.csv`: bad-news and disclosure-timing regressions.
- `tables/table_16_control_variable_descriptive_statistics.csv`: descriptive statistics for controls and public signals.
- `tables/table_18_software_versions.csv`: software versions used for reproducibility.
- `tables/table_19_model_hyperparameters.csv`: model tuning choices and selected hyperparameters.
- `tables/table_20_event_study_sample_construction.csv`: event-study sample construction steps.
- `tables/table_22_shap_importance.csv`: SHAP variable contribution table.
- `tables/table_23_size_heterogeneity.csv`: size-split heterogeneity test for the bad-news disclosure-timing relation.
- `tables/table_04_bad_news_prediction_metrics.csv`: out-of-sample prediction metrics.
- `tables/table_05_incremental_auc_bootstrap.csv`: bootstrap test for incremental AUC from disclosure schedules.
- `tables/table_07_event_study_car_metrics.csv`: market-adjusted event-window CARs.
- `tables/table_10_economic_value_real_returns.csv`: real-return economic value test.
- `figures/figure_02_prediction_roc_incremental_value.png`: ROC comparison.
- `figures/figure_09_sample_trends.png`: sample size, bad-news rate, and late-disclosure rate by year.
- `figures/figure_10_core_regression_coefficients.png`: coefficient plot for core disclosure-timing regressions.
- `figures/figure_11_prediction_auc_heatmap.png`: clean AUC heatmap comparing models and feature sets.
- `figures/figure_04_shap_summary_public_signals.png`: SHAP summary plot for public bad-news prediction.
- `figures/figure_05_event_study_late_vs_early.png`: event-study CAR plot with 95% confidence intervals.
- `figures/figure_06_economic_value_real_returns.png`: economic value plot.

## Main Findings
1. Bad-news firms disclose later. In the fixed-effects LPM, realized bad news increases the probability of being in the latest disclosure quartile by 0.155 (15.5 percentage points, p=1.53e-40).
2. Bad-news firms also postpone more often. The postponement coefficient is 0.072.
3. Disclosure timing alone adds modest out-of-sample prediction value: LightGBM AUC rises by 0.005 when full schedule variables are added to lagged fundamentals, but the bootstrap p-value for a positive gain is 0.180. This should be reported as suggestive rather than decisive.
4. The broader public-information package, especially earnings forecasts, is highly predictive of realized bad news. This is useful for a practical risk-screening interpretation, but it should not be oversold as a pure timing effect.
5. The annual-report event-study reaction is not statistically strong. That weak event reaction is economically interpretable: much of the bad news appears to be anticipated through forecasts and disclosure schedules before the annual report date.
6. Size heterogeneity is limited. The large-minus-small difference in the bad-news effect is 0.000 with p=0.998, implying that the disclosure-timing signal is broad rather than confined to one size group.

## LightGBM Test-Set Metrics
| feature_set                      |   test_auc |   test_average_precision |   top_decile_bad_news_rate |
|:---------------------------------|-----------:|-------------------------:|---------------------------:|
| Lag fundamentals                 |   0.751967 |                 0.543988 |                   0.65625  |
| Fundamentals + full schedule     |   0.757296 |                 0.555837 |                   0.665179 |
| Full public signals (+ forecast) |   0.991041 |                 0.972738 |                   0.991071 |

## Limitations
- The event-study module uses a 240-event sample for runtime and API stability; expanding it is straightforward because all price data are cached by stock code.
- Short-window event returns use unadjusted close prices from AkShare `stock_zh_a_daily`; for a few-day window this is acceptable, but a full paper should use consistently adjusted returns.
- This paper does not identify disclosure timing as an exogenous causal treatment. It studies whether public disclosure-scheduling behavior is informative and economically useful.

## Reproducibility
- Full Python code is stored in `final/improved_version_disclosure_timing/scripts/disclosure_timing_project.ipynb`; the executed notebook is `final/improved_version_disclosure_timing/scripts/disclosure_timing_project_executed.ipynb`.
- The notebook downloads or reads cached AkShare data, cleans annual-report schedules and earnings forecasts, merges them by stock code and fiscal year with the financial panel, constructs lagged controls, estimates regressions and prediction models, and writes all tables/figures to this output folder.
- Repository URL: https://github.com/George-hardworking/data-science-in-empirical-economics
- Software versions are written to `tables/table_18_software_versions.csv`.

## Interpretation
This design does not claim that disclosure timing is an exogenous causal treatment. Instead, it uses the A-share annual-report appointment system as a public information environment and tests whether scheduling choices are informative about bad news and downside market reactions. That makes the contribution closer to the course examples: a public data source is transformed into an economically meaningful, out-of-sample risk signal with practical value.
