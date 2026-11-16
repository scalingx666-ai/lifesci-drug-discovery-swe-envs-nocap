# Issue

**Title:** Cuik reactmaker

## Description

# Add cuik-molmaker CGR reaction featurization path

> Depends on: NVIDIA-Digital-Bio/cuik-molmaker#[4] — opening as draft until that releases on PyPI.

## Description

Extends the existing `--use-cuikmolmaker-featurization` flag to support **reaction property prediction** via a C++-accelerated CGR featurization path. Adds 280 lines across 10 files; no existing logic is modified.

New classes:
- `LazyReactionDatapoint` — stores reaction SMILES strings, deferring `Chem.Mol` construction to batch time
- `CuikmolmakerReactionDataset` — overrides `__getitems__` to dispatch the full DataLoader batch in a single C++ call
- `CuikmolmakerCGRFeaturizer` — calls `cuik_molmaker.batch_reaction_featurizer(...)` and returns `BatchCuikMolGraph`

The C++ side is a faithful reimplementation of `CondensedGraphOfReactionFeaturizer` — all 6 `RxnMode` variants, `keep_h`/`add_h` semantics, and node ordering match exactly.

## Example / Current workflow

```python
# Current: Python CGR featurizer, ~950 µs/reaction regardless of batch size
chemprop train --data-path reactions.csv --reaction-columns rxn --target-columns ea \
    --epochs 50
# On RGD1 (354k reactions): featurization dominates, ~53 s/epoch
```

## Bugfix / Desired workflow

```python
# With this PR: single C++ batch call per DataLoader batch
chemprop train --data-path reactions.csv --reaction-columns rxn --target-columns ea \
    --epochs 50 --use-cuikmolmaker-featurization
```

Speedup benchmarking can be found [here](https://github.com/akshatzalte/cuik-reactmaker-benchmarks)

## Relevant issues

N/A

## Checklist
- [x] linted with flake8?
- [ ] unit tests added? *(golden-output regression tests are in the cuik-molmaker repo)*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d0fdf45db6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.