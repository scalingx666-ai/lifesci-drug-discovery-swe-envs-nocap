# Issue

**Title:** Support pathlib.Path in MolFromSDFTransformer

## Description

.

`MolFromSDFTransformer.transform` only accepted `str`. A `pathlib.Path` broke at `X.endswith(".sdf")` (Path has no `.endswith`).

Fix: normalize the input with `os.fspath(X)` at the start of `transform`, so a `Path` is accepted while `str` paths and raw SDF text pass through unchanged. Type hint and docstring widened to `str | Path`.

Scope: this addresses the reader named in the issue. `MolToSDFTransformer` takes its output path as a constructor param constrained to `[str]`; happy to extend that to `PathLike` in a follow-up if you want the writer to accept `Path` too.

Verified: `pytest tests/preprocessing/input_output/sdf.py` → 11 passed (added `test_mol_from_sdf_accepts_path_object`); `ruff check` + `ruff format` clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b59c54717be7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.