# FleetGuard
Uncertainty-Aware Predictive Maintenance &amp; Resource-Constrained Maintenance Scheduling

## FD001 analysis notebooks

Each notebook is designed to run independently from the processed files in
`data/processed/`; later notebooks rebuild their own model-derived inputs and
do not require a previous notebook's kernel state.

1. `notebooks/02_rul_prediction.ipynb` — train and evaluate RUL prediction models.
2. `notebooks/03_uncertainty_estimation.ipynb` — estimate prediction uncertainty.
3. `notebooks/04_risk_assessment.ipynb` — rank fleet risk.
4. `notebooks/05_maintenance_optimization.ipynb` — optimize the maintenance schedule.
5. `notebooks/06_explainability.ipynb` — explain predictions with SHAP.

Run a notebook from the repository root or from `notebooks/`. Results and
figures are written under `outputs/`.
