# featuregraph-smoothing-core

Code and data behind "A Compiler-Level Account of Smoothing-Parameter
Choice." Contains `OscillationConfig` (the construction used throughout
the paper), a BIDMC data loader, and the validation logic behind the
paper's human-annotation results.

## Install

```bash
pip install -e .
```

## Reproduce the paper's results

```bash
pytest tests/ -v
```

Two tests are skipped by default, since they need a live download from
PhysioNet. Their skip reasons record the exact confirmed results;
remove the `@pytest.mark.skip` decorator above either one and rerun to
reproduce it directly:

- `test_reproduces_paper_correlation_and_ratio_range` — the paper's
  population correlation (0.39) and ratio range (1.14x–40.25x) across
  all 53 BIDMC subjects.
- `test_bidmc_peak_matched_recall_excluding_flagged_subjects` — the
  paper's human-annotation recall results (Table 1), N=32.

## Using OscillationConfig directly

```python
from featuregraph_smoothing_core.behaviors.oscillation import OscillationConfig

config = OscillationConfig(signal="respiration", smooth_window=100)
added = config.add_primitives(df, "subject")
summary = config.summarize(added, ["subject", config.trough_event_id_col])
```

## What's here

- `src/featuregraph_smoothing_core/` — the package
- `notebooks/bidmc_visual_demo.ipynb` — the code that produced Figure 1
- `artifacts/paper/compiler/smoothing.md` — the paper manuscript
- `tests/` — the full test suite

## Citation

Software: https://doi.org/10.5281/zenodo.22947447

## License

MIT. See `LICENSE`.
