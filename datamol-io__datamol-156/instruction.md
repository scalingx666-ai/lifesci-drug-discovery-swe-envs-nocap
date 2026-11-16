# Issue

**Title:** Add utility functions to manipulate atom positions and properties

## Description

Checklist:

- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [x] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

See the changelogs for details. The goal is to make it easier to manipulate atom properties and positions in order to be able to more easily reconstruct a molecule from an array of positions and a mapped SMILES with atom numbers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20cdbd169eda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.