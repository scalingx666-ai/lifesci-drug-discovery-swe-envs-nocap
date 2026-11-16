# Issue

**Title:** Set conf_id property in MolFromSDFTransformer

## Description

## Changes

.

`MolFromSDFTransformer` returned plain `Mol` objects without the `conf_id` integer property, while the convention elsewhere (`ConformerGenerator`, the 3D fingerprints, `MolToSDFTransformer`) is to read the conformation from `conf_id`. As a result, molecules loaded from SDF — which already carry a conformation — couldn't be passed to 3D fingerprints:

```python
mols = MolFromSDFTransformer().transform("mols.sdf")
RDFFingerprint().transform(mols)
# TypeError: Passed data must be molecules (RDKit Mol objects) and each must have conf_id property set.
```

Molecules with a conformation are now returned as `PropertyMol` with `conf_id` set to the ID of the 0th conformer, for all read paths (file, raw text, multithreaded). Molecules that failed to parse (`None`) or have no conformers are returned unchanged.

Added tests for the file and raw-text paths; both fail before the change and pass after. Full test suite (`pytest tests --ignore=tests/datasets`, 1546 passed) and ruff are green.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`) — no doc source changes; the class docs come from the updated docstring

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41dbec017db9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.