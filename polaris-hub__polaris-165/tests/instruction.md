# Issue

**Title:** Improving token errors and quickstart guide

## Description

## Changelogs

- Updated the quickstart guide to include a section about logging in prior to interacting with artifacts on Polaris
- Updated the handling of `client.request` errors such that client-side token errors produce a more useful error message to the user
- Updated the `client.base_request_to_hub` method to provide a more meaningful error message to users when their token expires

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._ Yes:  
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bace27e01b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.