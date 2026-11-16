# Issue

**Title:** feature: polaris fsspec basic read only implementation

## Description

## Changelogs

Integrated a read-only version of [Hadrien's POC](https://github.com/polaris-hub/polaris-fs/blob/main/polarisfs/client/fs.py) for the Polaris FSSpec. Some of the major changes include:
- Added a new endpoint in the client to be able to read the zarr file of a dataset.
- Added a new submodule in the hub folder, `polarisfs.py` which contains the FSSpec.
- For read-only implementation, the FSSpec currently supports the `ls` and `cat_file` operations.

#### More details of the FSSpec Implementation:
- The `ls` function makes a GET request to the Hub's api storage ls endpoint which returns an array of dictionaries, containing the files and directories within a given path in the Cloudflare R2 bucket.
- In the `ls` function, the prefix is required to be removed from each entry as the path provided to the Zarr store contains only the `{path}/...`, and not the `dataset/{owner}/{name}/{path}...`
- The `cat_file` makes a GET request to the Hub's api storage endpoint to obtain a signed URL for a given path and follows the redirect to obtain the contents of the file.
- The `cat_file` needed to have an specified timeout to avoid ending prematurely for larger sized zarr files

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._



Linked to:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e3083030b99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.