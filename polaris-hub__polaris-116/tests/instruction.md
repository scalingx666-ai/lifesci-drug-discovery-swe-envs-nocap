# Issue

**Title:** Test that all rows of a competition test set will have at least a value

## Description

## Changelogs

- adds some validation on competition creation to check that all test rows will have at least one value in a target column

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [-] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

This is a small improvement discussed with Andrew before his vacation. We want to make sure that you can't create a competition where there is missing test data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44c5d7f8fac8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.