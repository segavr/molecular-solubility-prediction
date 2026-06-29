# Molecular Solubility Prediction (ESOL)

This repository contains my first project on molecular property prediction. I use the ESOL dataset to predict aqueous solubility from simple RDKit descriptors.

## Project goal

The goal is to build and understand simple baseline models that predict measured log solubility (in mols per litre) from molecular strugrams.

## Dataset

- ESOL dataset (Delaney solubility data), commonly used in MoleculeNet benchmarks for solubility prediction.
- Target: `measured log solubility in mols per litre`.
- Input features: RDKit descriptors such as molecular weight (MW), LogP, topological polar surface area (TPSA), number of H-bond donors (HBD), number of H-bond acceptors (HBA), and number of rotab:11][web:8]

## Methods

1. Load the ESOL dataset into a pandas DataFrame.
2. Convert SMILES strings to RDKit molecule objects.
3. Compute RDKit descriptors (MW, LogP, TPSA, HBD, HBA, RotatableBonds).
4. Split the data into train and test sets.
5. Train two baseline regression models:
   - Linear Regression
   - Random Forest Regressor
6. Evaluate models with RMSE, MAE, t set. [web:11][web:16]

## Results (baseline)

On the held-out test set (random 80/20 split):

- Linear Regression: RMSE ≈ 1.10, R² ≈ 0.74
- Random Forest: RMSE ≈ 0.83, R² ≈ 0.85

These numbers show that the non-linear Random Forest model fits the ESOL data bee linear model. [web:11][web:16]

## Figures

The `figures/` folder contains:

- `esol_logp_tpsa_scatter.png`: ESOL molecules in LogP–TPSA space.
- `esol_rf_pred_vs_measured.png`: Random Forest predicted vs measured solubility plot.

I plan to reference these figures in a short report-style notebook and in future applications. [web:11]

## Repository structure

- `data/` – raw and processed ESOL data (`esol.csv`, `esol_descriptors.csv`).
- `notebooks/`
  - `01_esol_data_loading.ipynb` – data loading and RDKit descriptor calculation.
  - `02_esol_modeling.ipynb` – model training, evaluation, and plots.
- `figures/` – plots used in this README and for documentation.
- `results/` – CSV file with baseline model metrics (`esol_baseline_models.csv`).
- `src/` – (planned) reusable helper functions for data and modeling.
- `models/` – (optional) place to store trained model artifacts.
- `README.md` – project description (this file).

## How to run

1. Create and activate the `molprop` conda environment.
2. Install required packages (pandas, numpy, scikit-learn, matplotlib, seaborn, rdkit, jupyter).
3. Launch Jupyter Notebook from the project root.
4. Run `notebooks/01_esol_data_loading.ipynb` first.
5. Then run `notebooks/02_esol_modeling.ipynb`.

## Next steps

- Add more descriptors and try other models (e.g. XGBoost or simple neural networks).
- Compare random vs scaffold splits to be closer to MoleculeNet benchmark practice.
- Et to the Lipophilicity dataset for logD prediction.