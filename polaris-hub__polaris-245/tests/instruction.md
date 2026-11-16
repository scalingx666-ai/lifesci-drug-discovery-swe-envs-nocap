# Issue

**Title:** chore: Add a CI job to run tests in Conda, to detect dependency failure earlier

## Description

## Changelogs

- Add a GitHub Actions job to run the test suite under a Conda environment
- Update the dependency list by removing unused ones

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Since we've been tripped by some dependendencies that don't have all platforms supported in Conda, adding a CI flow that will run the tests from a clean Conda environment should raise these issues earlier.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe9da3a38d9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.