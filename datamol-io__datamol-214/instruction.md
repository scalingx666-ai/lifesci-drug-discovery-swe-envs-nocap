# Issue

**Title:** Improve the ChEMBL drugs dataset

## Description

Purpose: For datamol to have a dataset of all approved drugs in ChEMBL that contains metadata columns such as ChEMBL ID, date of approval, etc.

## Changelogs

Added chembl_approved_drugs to datamol/data/
Modified dm.data.chembl_drugs() to leverage it
Adapted docstring to explain how it was generated
Modified unit tests
Added notebooks folder with code that generated chembl_approved_drugs.parquet

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3c4a38cc217`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.