# Issue

**Title:** chore: Update dataset manifest build

## Description

## Changelogs

- Update the way we build the Zarr archive manifest to use a single PyArrow table. This yields a reduction of ~90% in size of the resulting manifest, probably due to better compression. (A manifest of 3708 files went from 2.7MB to 119KB.)

---

_Checklist:_

- ~[ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- ~[ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- ~[ ] _Update the API documentation if a new function is added, or an existing one is deleted._~
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dbb441eaeb6f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.