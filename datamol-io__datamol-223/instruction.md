# Issue

**Title:** Allow additional args for colors in lasso

## Description

## Changelogs

- Add support for some drawer options and fix edge cases where user-provided options are not properly handled. This concerns mostly the atom and bonds highlighting and color system

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [x] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

This PR allows us to now do something like this:

```python
  smi = "CO[C@@H](O)C1=C(O[C@H](F)Cl)C(C#N)=C1ONNC[NH3+]"
  mol = dm.to_mol(smi)
  smarts_list = "CONN"
  highlight_atoms = [4, 5, 6]
  highlight_bonds = [1, 2, 3, 4]
  highlight_atom_colors = {4:(186,85,211), 5:(186,85,211), 6:(186,85,211)}
  highlight_bond_colors = {1:(186,85,211), 2:(186,85,211), 3:(186,85,211), 4:(186,85,211)}
  dm.lasso_highlight_image(mol, smarts_list, highlight_atoms=highlight_atoms, highlight_bonds=highlight_bonds, highlight_atom_colors=highlight_atom_colors, highlight_bond_colors=highlight_bond_colors, continuousHighlight=False, circleAtoms=False)
```
See the purple part of the molecule here. 
<img width="764" alt="image" src="https://github.com/datamol-io/datamol/assets/5290110/ae46984e-4928-4f1b-9f04-a65825f2f1ac">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d1cde1c611d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.