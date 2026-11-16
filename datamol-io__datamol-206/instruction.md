# Issue

**Title:** Better control of the circular layout in `circle_grid`

## Description

## Changelogs

- Remove a left hover print statement in `lasso_highlight_image()`.
- Add a random seed in `MolsCircleGrid` and `circle_grid` to better control the circular layout.
- Add the ability to fix the starting angle in `circle_grid`
- Allow to input colors as hex string in addition to rgb and rgba.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ff85614ec4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.