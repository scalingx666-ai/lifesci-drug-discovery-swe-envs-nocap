# Issue

**Title:** Allow an empty train partition to support test-set only (e.g. zero-shot) benchmarks

## Description

This PR enables the definition of zero-shot benchmarks by allowing the train partition of `BenchmarkSpecification` to be an empty list.  

## Changelogs

- No more `InvalidBenchmarkError` is raised when `v[0]` is empty in `_validate_split`
- Error message and docstring was adjusted accordingly
---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._ #131 
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1278da004f71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.