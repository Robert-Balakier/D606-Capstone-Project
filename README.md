# D606 Capstone Project

## Project objective

This capstone asks whether a logistic regression model can be constructed to predict elevated environmental microbial results using information available before a sample result is known. The formal alternative hypothesis requires the primary model's held-out accuracy to exceed 70%, while precision, recall, F1, confusion matrices, and average precision are used to assess practical usefulness under severe class imbalance.

## Data and analysis workflow

- `Cleaning.ipynb` documents how the raw Excel data were cleaned. It is not the main analysis notebook.
- `environmental_monitoring_microbiology_2022_2026.csv` is the final cleaned dataset and the sole modeling source.
- `Main.ipynb` contains validation, target creation, exploratory analysis, leakage-safe preprocessing, model evaluation, interpretation, hypothesis testing, and conclusions.
- `D606_Capstone_Dataset.xlsx` is the raw source retained for provenance; it is not loaded by `Main.ipynb`.

The binary target is `Elevated_Result`: acceptable or blank `Action/Alert Count` values map to 0, while Alert and Action map to 1. Standard logistic regression is the primary model. Balanced logistic regression and Random Forest are comparison models.

## Repository structure

```text
Cleaning.ipynb
Main.ipynb
environmental_monitoring_microbiology_2022_2026.csv
D606_Capstone_Dataset.xlsx
outputs/
  model_metrics.csv
  logistic_coefficients.csv
  *.png
requirements.txt
```

## Run the analysis

From the repository root, create or activate a Python environment and install the dependencies:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Open `Main.ipynb`, select the `.venv` Python kernel, and run all cells from top to bottom. The notebook loads the cleaned CSV directly and does not require `Cleaning.ipynb` to be run first. Running it recreates the tables and figures in `outputs/` using `random_state=42`.

