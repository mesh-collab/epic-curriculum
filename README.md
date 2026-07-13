# EPIC Curriculum

Introductory Python and Jupyter tutorial notebook for the EPIC (Exploring Particle
Physics Integrated with Computing) summer program, run under the MESH (Mississippi
EPSCoR Scientific Hub) partnership.

## Notebook

- `notebooks/00_python_and_jupyter_intro.ipynb` - Jupyter basics, core Python
  (variables, lists, conditionals, loops), particle physics context, GitHub workflow,
  building histograms, and applying a data cut with pandas.

## Setup

```bash
uv sync
uv run python -m ipykernel install --user --name=epic-curriculum --display-name "EPIC Curriculum"
uv run jupyter lab
```

Open the notebook and make sure the kernel in the top-right says **EPIC Curriculum**.
