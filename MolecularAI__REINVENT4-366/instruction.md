# Issue

**Title:** fix: return PMI scores in configured endpoint order

## Description

The PMI component always returns the npr1 scores first and the npr2 scores second, whatever order the endpoints are in the config. If the npr2 endpoint is listed first, its name, transform and weight get applied to the NPR1 values and the other way round. Nothing warns about it, so the reward and the CSV/TensorBoard columns are quietly wrong. `configs/SCORING.md` recommends exactly this two-endpoint setup.

Repro: butadiyne (`C#CC#C`) is linear, so NPR1 is about 0 and NPR2 is about 1 for any conformer.

```python
import numpy as np
from reinvent.scoring.scorer import Scorer

cfg = {"type": "arithmetic_mean", "component": [{"pmi": {"endpoint": [
    {"name": "npr2 endpoint", "weight": 1, "params": {"property": "npr2"}},
    {"name": "npr1 endpoint", "weight": 1, "params": {"property": "npr1"}}]}}]}
res = Scorer(cfg)(["C#CC#C"], np.array([True]), np.array([True]))
c = res.completed_components[0]
print(list(zip(c.component_names, c.transformed_scores)))
```

On main, "npr2 endpoint" gets 3.5e-05 (that's NPR1) and "npr1 endpoint" gets 0.99997. With this change they get 0.99997 and 3.5e-05.

Changes in `comp_pmi.py`:
- `__call__` returns one score array per configured endpoint, in config order. The scores were added with `if "npr1" in ...` / `if "npr2" in ...`, which fixed the order and capped the output at two arrays, while names, transforms and weights are matched to the scores by position. This also fixes two `npr1` endpoints returning a single array.
- Property names other than `npr1`/`npr2` now raise a `ValueError` at setup. Before, a typo like `nrp2` was accepted and that endpoint's scores were dropped silently (two endpoint names, one score array). An empty property list still raises the existing error.

Tests: three new unit tests in `test_comp_pmi.py` (endpoint order, repeated property, unknown property). The order test uses the linear molecule, so it doesn't depend on the conformer. All three fail on main and pass with the fix. `tests/reinvent_plugins/unit_tests` and `tests/scoring/unit_tests` give 118 passed. The one failure, `test_comp_mol_volume`, also fails on unmodified main with RDKit 2026.03 and is unrelated.

The only behaviour change: a config with an unknown `property` value now fails at startup instead of running with that endpoint missing. If you'd rather keep those configs running, I can turn it into a warning.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `660d2c9cec9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.