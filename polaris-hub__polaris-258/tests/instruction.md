# Issue

**Title:** `Subset.as_dataframe()` hides targets instead of raising an error

## Description

## Changelogs

- `Subset.as_dataframe()` would raise an error when called on a test set (which hides its targets), this PR allows method to work, just doesn't return targest

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [ ] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Resolves

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6747c58ff656`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.