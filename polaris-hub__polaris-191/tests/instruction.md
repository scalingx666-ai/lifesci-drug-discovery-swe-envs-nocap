# Issue

**Title:** XL Datasets: Upload

## Description

## Changelogs

- Updated the `DatasetV2.upload_to_hub` method to call the `client.upload_dataset` method in the PolarisHubClient class
- Added some conditional logic to call `client._upload_v1_dataset` or `client._upload_v2_dataset` depending on the type of the dataset object passed as an argument
- Added the `client._upload_v2_dataset` method to handle uploading V2 datasets
- Leverage `StorageSession` and the storage tokens to upload the manifest and Zarr archive to the storage backend

~Currently on-hold until  is addressed:~
~- Leveraging storage JWTs in `client._upload_v2_dataset`~
~- Leveraging storage JWTs in `client._get_v2_dataset` ~
**Edit:** Storage JWT work is done.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e402f9d58d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.