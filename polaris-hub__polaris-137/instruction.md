# Issue

**Title:** Only adding zarrRootPath field to datasets that use Zarr

## Description

## Changelogs

Updating the `client.upload_dataset` method to only add the `zarrRootPath` field to datasets which make use of Zarr. Otherwise, datasets which do not use make use of Zarr will fail a validation check and cannot be uploaded. 

---

_Checklist:_

~- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
~- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c93f849d4a52`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.