# EPIC Curriculum

Introductory Python and Jupyter tutorial notebook for the EPIC (Exploring Particle
Physics Integrated with Computing) summer program, run under the MESH (Mississippi
EPSCoR Scientific Hub) partnership.

## Notebooks

- `notebooks/00_python_and_jupyter_intro.ipynb` - Jupyter basics, core Python
  (variables, lists, conditionals, loops), particle physics context, GitHub workflow,
  building histograms, and applying a data cut with pandas.
- `notebooks/neutrino_part1_oscillation_spectra.ipynb` - NOvA/DUNE toy near/far
  detector energy spectra via `nuosclab`, Poisson toy-statistics fluctuations, and
  finding the oscillation dip in an overlay/ratio plot.
- `notebooks/neutrino_part2_parameter_explorer.ipynb` - turns the spectrum from part 1
  into a parameter study, using `nuosclab` widgets to vary experiment, θ₂₃, Δm²₃₂, and
  δCP and see how the oscillation pattern responds.
- `notebooks/neutrino_bonus_nsi_explorer.ipynb` - extension notebook exploring
  Non-Standard Interactions (NSI): a single ε_eμ/δ_eμ knob layered on top of the
  standard three-flavor picture from part 2.

## Setup

```bash
uv sync
uv run python -m ipykernel install --user --name=epic-curriculum --display-name "EPIC Curriculum"
uv run jupyter lab
```

Open the notebook and make sure the kernel in the top-right says **EPIC Curriculum**.

## Linting

Before committing a new notebook or a variant of an existing one, run [Ruff](https://docs.astral.sh/ruff/)
(config already set up in `pyproject.toml`, covers `.ipynb` files directly):

```bash
uv run ruff check notebooks/      # lint
uv run ruff format notebooks/     # auto-format
```

Both must pass clean before committing. A few other things to check by hand:

- **Clear stray outputs/metadata** before committing - re-running a notebook adds cell
  outputs and `metadata.execution` timestamps that just add noise to diffs:
  ```bash
  uv run jupyter nbconvert --clear-output --inplace notebooks/your_notebook.ipynb
  ```
- **Run the whole notebook top to bottom** (Kernel > Restart Kernel and Run All Cells,
  or `uv run jupyter execute notebooks/your_notebook.ipynb`) to confirm it works in a
  fresh kernel, not just in whatever order you happened to run cells while editing.
- If a cell is **intentionally broken** (e.g. a debugging exercise), tag it
  `raises-exception` (Jupyter: View > Cell Toolbar > Tags) so tooling doesn't treat the
  error as a real bug.
