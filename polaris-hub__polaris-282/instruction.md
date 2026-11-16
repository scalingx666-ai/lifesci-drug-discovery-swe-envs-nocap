# Issue

**Title:** fix: Prevent missing FastPDB on Conda install

## Description

## Changelogs

- Moved FastPDB from a pip dependency to a conda-forge dependency

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Adresses issue #276.

By moving the FastPDB dependency to the conda-forge list, we'll prevent users with certain environment configuration from installing an incomplete Polaris.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92bb0bf7d821`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.