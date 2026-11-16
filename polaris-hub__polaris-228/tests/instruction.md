# Issue

**Title:** Testing: Added Windows to CICD testing matrix, add hub integration test and fix errors

## Description

## Changelogs

- Added Windows to the CICD testing matrix.
- Using #221, add integration test with the Hub.
- Switched to `uv` instead of `mamba` for the CICD
- Fix #226 

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

I created a dedicated test user in Clerk for this. It's credentials have been added to the secrets of this Github repository.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75bea60b0ef4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.