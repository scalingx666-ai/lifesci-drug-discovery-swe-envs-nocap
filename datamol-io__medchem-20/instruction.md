# Issue

**Title:** Fix issues with loading data on python 3.9

## Description

## Changelogs

- Fix errors due to `importlib.resources`  not being able to parse data from `medchem.data` on py<3.10

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [ ] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

Discussion related to this PR can be found in #19 . This PR effectively

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a63bd6ff52e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.