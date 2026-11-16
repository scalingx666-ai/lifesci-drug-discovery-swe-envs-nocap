# Issue

**Title:** feat: add to_binary(), to_dict(), from_dict(); modify to_mol()

## Description

## Changelogs

- add `datamol.convert.to_binary()` using `Mol.ToBinary()`
- extend `datamol.mol.to_mol()` to accept a binary string as input
- add `datamol.convert.to_dict()` using `rdkit.Chem.rdMolInterchange`
- add `datamol.convert.from_dict()`
- add corresponding tests

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [x] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [ ] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

Related to #230

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e175fd609a25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.