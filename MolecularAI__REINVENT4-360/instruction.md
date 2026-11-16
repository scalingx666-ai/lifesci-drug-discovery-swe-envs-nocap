# Issue

**Title:** fix: chain SMILES actions and only map '.' to '|' where '|' is a valid token

## Description

`read_smiles_csv_file` applied every action to the *original* SMILES (`smiles = action(orig_smiles)`) instead of chaining them, so e.g. `standardize` + `randomize` did not compose and salt removal never happened before token validation. Actions are now chained (`smiles = action(smiles)`).

Additionally, `.` (salt/R-group separator) was unconditionally replaced with `|`, which produced an unsupported `|` token for Reinvent/Mol2Mol ( reproduction). The replacement is now only done when `|` is a valid token (LinkInvent).

## Tests
- regression tests for action chaining and for the `|` handling in LinkInvent vs Reinvent vocabularies.

`pytest tests/utils/test_config_parse.py` -> 13 passed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43094673bf0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.