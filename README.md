# Sleep Duration and First-Year GPA: Does the Association Vary Across the Sleep Range?

Code submitted with the bachelor thesis of **Anass Maata** (BSc Cognitive Science & Artificial Intelligence, Tilburg University; supervisor: Dr. Silvy Collin).

The thesis asks to what extent the association between objectively measured (Fitbit) sleep duration and end-of-term GPA varies across the sleep-duration range after accounting for previous GPA. It estimates the shape of the adjusted association across the whole observed sleep range with a generalized additive model (GAM), compares it with a linear regression model, summarizes the curve with the GPA difference linked to one extra hour of sleep (5→6, 6→7, 7→8 h) with a cohort-stratified bootstrap, checks the residuals, repeats the analysis without two influential short sleepers and without each cohort in turn, and briefly checks prediction for unseen cohorts.

## Files

| File | What it is |
|---|---|
| `thesis_analysis.ipynb` | **Main analysis.** Reproduces every number, table and figure in the report, step by step with plain-language explanations. |
| `requirements.txt` | Python packages and tested versions. |
| `output/figures/`, `output/tables/` | Figures and tables created by the main notebook. |
| `output/cache/` | Saved bootstrap results, created on the first run (not included in the submission). |

## Data

Public dataset *Nightly sleep time and GPA in first-years* (Creswell et al., 2023, *PNAS*, https://doi.org/10.1073/pnas.2209123120), from the CMU Statistics & Data Science Data Repository: https://cmustatistics.github.io/data-repository/psychology/cmu-sleep.html. Download `cmu-sleep.csv` and place it next to the notebook. Ownership remains with the original authors.

## How to run

1. `pip install -r requirements.txt`
2. Open `thesis_analysis.ipynb` (VS Code or Jupyter) and run all cells.
3. The first run takes about 5–10 minutes (two bootstraps of 1,000 samples); the results are then saved in `output/cache/`, so later runs take under a minute. To run the bootstraps again, set `USE_CACHE = False` in the settings cell or delete `output/cache/`. All settings (seed 2026, number of bootstrap samples, spline settings) are in one cell at the top.

## Report ↔ notebook

| Report | Notebook output |
|---|---|
| Table I | `table1_descriptives.csv` |
| Fig. 1 | `fig1_sleep_distribution` |
| Fig. 2 | `fig2_adjusted_curves` |
| Table II | `table2_per_hour_differences.csv` |
| Fig. 3 | `fig3_leave_one_cohort_out` (+ `table_leave_one_cohort_out.csv`) |
| Results IV-A (check against Creswell et al.) | `table_linear_vs_creswell.csv` |
| Results IV-A (residual check) | `table_residuals_by_sleep.csv` (+ `fig_extra_residuals`, not in report) |
| Results IV-C (why the lower bounds of the key comparison are about zero) | `table_bootstrap_K_split.csv` |
| Results IV-E | `table_prediction_across_cohorts.csv` |


