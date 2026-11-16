# Issue

**Title:** fix zero division error in conformers

## Description

## Changelogs

- Fixed a division-by-zero error in `dm.conformers.generate()` when `minimize_energy` is set to `True` and the molecule has no rotatable bonds. Below is a minimal example that reproduces the error:

  ```python
  import datamol as dm

  mol = dm.to_mol("c1ccccc1")
  dm.conformers.generate(mol, minimize_energy=True)
  ```

  Error message:
  ```
  /workspaces/datamol/datamol/conformers/_conformers.py:214: RuntimeWarning: invalid value encountered in scalar divide
  if E - minE <= ewindow and (E - minE) / rotatable_bonds <= eratio
  /workspaces/datamol/datamol/conformers/_conformers.py:214: RuntimeWarning: divide by zero encountered in scalar divide
    if E - minE <= ewindow and (E - minE) / rotatable_bonds <= eratio
  ```

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2619c610a6df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.