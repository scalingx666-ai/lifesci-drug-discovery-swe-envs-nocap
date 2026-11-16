# Issue

**Title:** Rdkit compat

## Description

Checklist:

- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [x] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

Make `dm.descriptors.n_heavy_atoms` compatible with rdkit 2021.03.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9255d0356a8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.