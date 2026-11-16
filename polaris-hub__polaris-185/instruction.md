# Issue

**Title:** Adding new Zarr manifest generation to DatasetV2 class

## Description

## Changelogs

- Updated the `DatasetV2` class to generate a new Zarr manifest and calculate its hash
- Updated testing to incorporate the new changes 
- Pending: Upload Zarr manifest on `upload_to_hub` call

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

- Let me know what you think about the placement of the `parquet` and `md5` functions in the`utils` folder. I'm not convinced this is the best place.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d4b718144e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.