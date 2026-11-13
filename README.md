# FleetGuard

**An AI/ML project for uncertainty-aware predictive maintenance and
resource-constrained maintenance scheduling.**

FleetGuard uses engine sensor time series from the NASA C-MAPSS turbofan
degradation dataset to estimate Remaining Useful Life (RUL), quantify
prediction uncertainty, prioritize fleet risk, and explore maintenance
decisions. The current notebook workflow focuses on the FD001 subset.

## Project workflow

The notebooks are designed to run in separate, fresh kernels. Notebook 01
prepares the processed FD001 data; notebooks 02–07 load those files and build
their own models and analysis rather than depending on variables or execution
order from another notebook.

1. [`notebooks/01_data_exploration.ipynb`](notebooks/01_data_exploration.ipynb) —
   validate raw FD001 data, build RUL labels, split engines without leakage,
   and save processed datasets.
2. [`notebooks/02_rul_prediction.ipynb`](notebooks/02_rul_prediction.ipynb) —
   engineer features, train and evaluate RUL prediction models.
3. [`notebooks/03_uncertainty_estimation.ipynb`](notebooks/03_uncertainty_estimation.ipynb) —
   estimate prediction uncertainty and evaluate interval calibration.
4. [`notebooks/04_risk_assessment.ipynb`](notebooks/04_risk_assessment.ipynb) —
   rank engines by fleet risk.
5. [`notebooks/05_maintenance_optimization.ipynb`](notebooks/05_maintenance_optimization.ipynb) —
   compare maintenance strategies under a technician-hour budget.
6. [`notebooks/06_explainability.ipynb`](notebooks/06_explainability.ipynb) —
   explain model predictions with SHAP.
7. [`notebooks/07_dashboard.ipynb`](notebooks/07_dashboard.ipynb) —
   launch an interactive RUL, uncertainty, and what-if dashboard.

## Data

FD001 raw files are in `data/raw/`. Run notebook 01 to regenerate the
intermediate files in `data/processed/`. Notebooks 02–07 require those
processed files. The repository also contains additional C-MAPSS subsets in
`CMAPSSData/`; they are not currently used by these notebooks.

## Setup and run

Use Python with Jupyter Notebook support. Install the packages used across the
notebooks, including the optional analysis and dashboard dependencies:

```bash
python -m pip install numpy pandas matplotlib seaborn scikit-learn scipy joblib shap xgboost ipywidgets
```

Open the notebooks in Jupyter or VS Code and run each notebook from top to
bottom. They support running from either the repository root or the
`notebooks/` directory. Run notebook 01 first if the processed FD001 CSV files
are missing. The dashboard trains its own prediction and uncertainty models
and needs `xgboost` and `ipywidgets`.

## Outputs

Generated datasets, figures, models, and analysis tables are saved under
`data/processed/` and `outputs/` (including `outputs/figures/`,
`outputs/results/`, and `outputs/models/`).
