# halo-satellite-ml-pipeline

End-to-end SQL + Python data pipeline for satellite–halo analysis, including data curation, feature engineering, and machine learning modeling.

This project demonstrates a complete scientific/ML workflow:

feature engineering → model training → inference on external data

---

## Notebooks

### 01 – Feature Engineering (TNG300)
`01_tng300_pme_mass_estimation.ipynb`
- Load TNG300 simulation data
- Apply isolation selection
- Compute PME-based halo mass
- Generate training features

### 02 – Model Training (MLP)
`02_mlp_training_on_tng_features.ipynb`
- Train a PyTorch MLP model
- Save model checkpoints
- Visualize training performance

### 03 – Inference (SQL → MLP)
`03_inference_on_M81_satellites.ipynb`
- Query satellite features from a SQLite database using SQL
- Load trained checkpoint
- Run inference on the M81 satellite system

---

## Tech Stack
- Python (NumPy, pandas, PyTorch, Matplotlib)
- SQL / SQLite
- Jupyter notebooks

---

## Data
Due to data policy and size constraints, raw simulation and observational catalogs are **not included**.

You will need to provide:
- TNG300-derived features (Notebook 01 output)
- A SQLite database `satellites.db` with table `m81_satellites`

Example schema:

```sql
CREATE TABLE m81_satellites (
    name TEXT,
    log10_LK REAL,
    R_proj_kpc REAL,
    delta_v_kms REAL
);
