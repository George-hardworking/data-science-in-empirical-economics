# Assignment 2: Geospatial Analysis with CDL Data

## Project Information

| Item | Description |
|---|---|
| Course | IPEN 5810 — Data Science in Empirical Economics |
| Topic | Geospatial Analysis of California Cropland Data Layer (CDL) |
| Data | USDA CDL rasters (2022–2023), California county boundaries, crop dictionary |
| Framework | Geospatial Data Science, Remote Sensing |

## Overview

This assignment processes and analyzes 30m-resolution USDA Cropland Data Layer (CDL) raster files for California for the years 2022 and 2023. Using Rasterio for efficient block-based raster I/O and GeoPandas for vector boundary overlay, the notebook performs binary crop mapping, land-use area ranking, and pixel-level crop rotation analysis for almonds and grapes.

## Tasks

1. **Raster Visualization** (10 pts): Read and plot 2022 and 2023 CDL raster files with California county boundaries overlay. Implements downsampling for memory-efficient rendering.
2. **Top 10 Land Uses** (15 pts): Calculate top 10 land-use categories by pixel count using block-based processing to handle large rasters (>1 GB). Map codes to names using `cdl_dict.csv`.
3. **Binary Crop Mapping** (20 pts): Create and visualize binary rasters for almonds (Code 75) and grapes (Code 69) for both years, with county boundary overlays.
4. **Crop Rotation Analysis** (10 pts): Describe crop rotation patterns between almonds and grapes from 2022 to 2023 using pixel-level transition counts.
5. **State Transition Raster** (15 pts): Create a 5-class transition raster (almond→almond, grape→grape, almond→grape, grape→almond, other) with downsampled memory-safe implementation.
6. **Transition Visualization** (10 pts): Visualize the transition raster with custom colormap and clearly labeled legend.
7. **Analytical Approach** (10 pts): Describe data sources, methods, and modeling approach for answering crop rotation yield advantage questions.
8. **Challenges** (10 pts): Identify and explain three factors making accurate crop rotation analysis difficult (self-selection bias, data resolution mismatch, confounding environmental shocks).

## Repository Structure

```text
assignment2/
├── raw/
│   ├── 2022_30m_cdls_ca.tif          # 2022 CDL raster for California
│   ├── 2023_30m_cdls_ca.tif          # 2023 CDL raster for California
│   ├── california_counties.gpkg      # California county boundaries
│   └── cdl_dict.csv                  # Crop code-to-name dictionary
├── scripts/
│   └── assignment2_kaibiao.ipynb     # Main analysis notebook
├── output/                           # Generated outputs (figures, tables)
├── docs/
│   └── HW2_IPEN 5810_2026S.pdf      # Assignment instructions
└── README.md
```

## Main Analysis File

```text
scripts/assignment2_kaibiao.ipynb
```

The notebook is structured as:

1. Import packages (Rasterio, GeoPandas, Matplotlib, NumPy)
2. Load geographic data and raster files; reproject and downsample for plotting
3. Top 10 land-use calculation using block/window processing
4. Binary crop raster creation and visualization (almonds and grapes)
5. Crop rotation transition counting (pixel-level)
6. State transition raster construction and visualization
7. Analytical approach for crop rotation yield assessment (conceptual)
8. Challenges in accurate causal inference (conceptual)

## Environment

Python 3.10+ is recommended.

Key packages include:

- `pandas`, `numpy`
- `rasterio`
- `geopandas`
- `matplotlib`
- `collections` (Counter)

## How to Run

From the repository root:

```bash
jupyter nbconvert \
  --to notebook \
  --execute assignment2/scripts/assignment2_kaibiao.ipynb \
  --output assignment2_kaibiao_executed.ipynb \
  --output-dir assignment2/output \
  --ExecutePreprocessor.kernel_name=5020_env
```

Or run interactively in Jupyter using the `5020_env` kernel.

**Note:** The CDL raster files are large (>1 GB). The notebook uses block processing and downsampling to manage memory usage.

## Outputs

Running the notebook generates:

- Raster visualizations with county boundary overlays
- Top-10 land-use ranking tables for 2022 and 2023
- Binary crop maps for almonds and grapes (2022–2023)
- Crop rotation transition statistics
- State transition raster with custom colormap and legend

## Notes on Reproducibility

- Downsampling factor of 10× is used for plot rendering to prevent memory overflow.
- Block/window processing is used for pixel counting to handle rasters >1 GB.
- CRS reprojection ensures vector (county boundaries) and raster alignment.
- The notebook should be run from a clean kernel for final reproduction.

## License

This assignment is for course project submission and academic use.
