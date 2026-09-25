# featuregraph-smoothing-core

A minimal, frozen extract of FeatureGraph's state-detection code,
published specifically so the population-level results in the
smoothing paper (peak-count correlation and ratio spread across the
53-subject BIDMC cohort at different smoothing windows) can be
independently reproduced.

## What's in this repo

This package contains exactly one class, `OscillationConfig`, and its
three direct dependencies (`operators/states.py`, `operators/events.py`,
`operators/measures.py`) -- nothing else from FeatureGraph. It is not a
general-purpose release of the framework.

This is not the full FeatureGraph codebase. Actively developed
components live in a separate, private repository and are
not part of this package. This package exists solely to make one
specific published numerical claim checkable.

- `src/featuregraph_smoothing_core/` -- the package (`OscillationConfig`,
  its three operator dependencies, the BIDMC data loader, and a
  self-contained plotting module -- all real, verified source, no
  private dependencies remaining).
- `notebooks/bidmc_visual_demo.ipynb` -- the exact code that produced
  the paper's Figure 1 (the W=1 vs. W=100 single-subject illustration).
  Uses plain manual construction logic, not `OscillationConfig`, so it
  never depended on the private repo in the first place.
- `artifacts/paper/compiler/smoothing.md` -- the paper manuscript.

## Using this with the population-statistics script

The script that produces the paper's headline numbers imports:

```python
from state_detection.behaviors.oscillation import OscillationConfig
```

Once this package's three placeholder files are filled in and it's
installed (`pip install .` or `pip install featuregraph-smoothing-core`
once published), update that import line to:

```python
from featuregraph_smoothing_core.behaviors.oscillation import OscillationConfig
```

That one-line change is the only edit the script needs.

## Citation

Software: tagged release v1.0.0, archived at
10.5281/zenodo.22947447.

## License

MIT. See `LICENSE`.
