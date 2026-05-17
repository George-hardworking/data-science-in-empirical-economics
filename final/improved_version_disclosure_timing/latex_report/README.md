# LaTeX report

This folder contains the standalone final-project paper.

- `report.tex`: main LaTeX source.
- `compile.sh`: reproducible build script.
- `output/report.pdf`: compiled report.
- `build/`: temporary LaTeX build files when using `latexmk` or `pdflatex`.

Compile from the repository root with:

```bash
conda run --no-capture-output -n 5020_env bash final/improved_version_disclosure_timing/latex_report/compile.sh
```

The report imports figures from `final/improved_version_disclosure_timing/output/figures`, so the research notebook should be run before compiling the report.
