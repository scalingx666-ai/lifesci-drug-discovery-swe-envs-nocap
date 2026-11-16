# Issue

**Title:** Updating split validator to allow duplicates across test sets

## Description

## Changelogs

- Updating the `split` field validator in the `BenchmarkSpecification` model to check for duplicates _within_ individual test sets rather than _across_ all test sets
- Added test to ensure duplicates in a nested test set are caught
- Added test to ensure that duplicate indices are allowed across indices

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._ 
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9173e2a5c634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.