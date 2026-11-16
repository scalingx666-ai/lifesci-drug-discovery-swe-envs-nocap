# Issue

**Title:** Added a README field to the benchmark and dataset classes

## Description

## Changelogs

 

- Added a `readme` field to the `Dataset` and `BenchmarkSpecification` classes.

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

I considered two additional improvements, but didn't end up implementing these: 
- Show the formatted `readme` in Jupyter Notebooks for the respective representations. This is possible through `IPython.display`. However, I didn't want to go down the rabbit hole of improving the visual representation of these classes as I could quickly see this take up a lot of time and because it is not a priority as of now. 
- I looked around a bit for a more constrained type-hint than just a plain string, but I don't think there is a straight-forward answer (can you even distinguish normal strings from markdown strings with absolute certainty?).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dccf705f1c4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.