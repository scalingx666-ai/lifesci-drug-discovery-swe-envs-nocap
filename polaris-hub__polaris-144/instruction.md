# Issue

**Title:** Adding more informative error messaging due to potential JWT and Clerk data discrepancy

## Description

## Changelogs

Due to the potential discrepancy between claims in JWTs issued from the Hub and the true data in Clerk, we want to provide users with a more informative error message in the event of forbidden errors (for upload) and not found errors (for downloads). More specifically, we would like to suggest to the user to retry logging in to get a fresh JWT with up-to-date claims from Clerk.

- Added error messaging suggesting a re-login in the case of 403 forbidden errors when a user tries to upload a dataset, benchmark or result. 
- Added error messaging suggesting a re-login in the case of 404 not found errors when a user tries to retrieve a dataset or benchmark. 
- Updated the doc strings for the above client methods with a helpful note regarding the potential discrepancy.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._ 
    - This came about from another PR: 
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65a528023ef1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.