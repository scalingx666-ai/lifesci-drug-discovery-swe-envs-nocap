# Issue

**Title:** T008: Update biotite FieldQuery signature

## Description

## Description
Update `biotite`'s `FieldQuery` signature due to changes in PDB, see 

## Todos
- [x] Update `biotite` signature available with >=0.30.0
  - [x] `biotite>=0.30.0` available for `python>=3.7` via `conda` - perfect!
  - [x] What about Python versions <3.7? Install the latest biotite version from GitHub via `pip`
    ```python
    from platform import python_version
    if python_version() < "3.7":
        !pip install https://github.com/biotite-dev/biotite/archive/master.tar.gz
    ```
- [x] Rerun notebook: Results in changed PDB files due to MDAnalysis update (2.0.0); chain IDs set to X and elements gone (ok for our purposes, we won't need them downstream)
- [x] Update PDB query field URLs

## Questions
None

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0dcc78b6ee98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.