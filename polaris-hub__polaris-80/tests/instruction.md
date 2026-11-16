# Issue

**Title:** Hotfix: Added option to disable the checksum verification

## Description

## Changelogs

- Added the `verify_checksum` parameter to `load_dataset` and `load_benchmark`.
---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

  changed how the checksum is computed, which created errors when loading a dataset or benchmark from the hub. More generally, I think the checksum can be a little brittle so having a way to disable it seems good.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8936ae61fbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.