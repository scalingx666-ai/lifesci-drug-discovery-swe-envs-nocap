# Issue

**Title:** Preventing certain license types on dataset upload to hub

## Description

## Changelogs

- Added an enum for the Creative Commons licenses which we will accept for datasets being uploaded to the hub
- Added logic to throw an error on dataset upload attempts which contain an unsupported license type

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

- This PR is related to this issue -

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6bc49ba47ea2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.