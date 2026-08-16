# Koopman Semiflows

This repository contains a reproducible numerical notebook for studying Floquet modes and Koopman eigenfunctionals in a parabolic-semiflow benchmark. The implementation uses only forward-time evolution and is intended as a compact computational companion for the associated mathematical development.

## Model

The notebook uses a diffusive Stuart--Landau oscillator with homogeneous Neumann boundary conditions:

$$
\partial_t W
= d\,\partial_{xx}W + (1-|W|^2)W + i\omega_0W,
\qquad x\in(0,L).
$$

Calculations are carried out in a co-rotating frame using a cosine pseudospectral discretization and Strang splitting.

## Repository contents

- `experiments.ipynb` — the primary notebook. It contains the theory-facing explanations, computation cells, numerical tables, figures, captions, and experiment-specific discussion.
- `figures/` — PDF and PNG figures produced by the notebook.
- `results/` — CSV tables produced by the notebook.
- `NUMERICAL_ASSESSMENT.md` — supplementary project notes.

## Requirements

The notebook requires Python 3 with NumPy, SciPy, pandas, Matplotlib, and Jupyter/IPython. A minimal installation is:

```bash
python -m pip install numpy scipy pandas matplotlib ipython jupyter
```

## Running the notebook

1. Create and activate a Python environment with the requirements above.
2. Start Jupyter Lab or Jupyter Notebook from the repository root.
3. Open `experiments.ipynb` and run all cells from top to bottom.

The notebook regenerates the figures and CSV tables in the repository-relative `figures/` and `results/` directories. Numerical interpretations and experiment-level results are intentionally kept in the corresponding Markdown and code cells of the notebook.
