# Issue

**Title:** fix(examples): document atomic_grid features in download_model.py

## Description

The `download_model.py` C++ integration example crashes with `KeyError: 'atomic_grid_weights'` when run against the current `microsoft/skala-1.1` checkpoint: the functional requests the `atomic_grid_*` features, but the script's hand-maintained `feature_shapes` / `feature_labels` dictionaries were never updated to include them. These dictionaries are the only human-readable documentation of the model inputs in the repo, and nothing exercised them, so they silently went stale.

## Changes

- Document the three per-atom grid features in `download_model.py`:
  - `atomic_grid_weights` — per-atom-grid quadrature weights (the raw weights for integrating over each individual atomic grid, **not** Becke-partition-weighted, unlike `grid_weights`).
  - `atomic_grid_sizes` — number of grid points per atom.
  - `atomic_grid_size_bound_shape` — empty tensor whose first dim is `max(atomic_grid_sizes)`; carries no data and exists only to pass the static padding bound as a tensor shape (a TorchScript/LibTorch export detail).
- Add a `feature_dtypes` map and print per-feature dtype, since `atomic_grid_sizes` and `atomic_grid_size_bound_shape` are `int64`, not `float64`.
- Inline comments capture the fuller explanations for the two subtle features.

## Tests

Add `tests/test_download_model.py`, which:
- runs the script end to end (would catch the `KeyError` regression), and
- asserts every feature each published functional requests is present in all three documentation dictionaries, so they cannot drift out of sync again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88b66089cb94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.