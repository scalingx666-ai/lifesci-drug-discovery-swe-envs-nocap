# Issue

**Title:** feature: polaris fsspec write implementation

## Description

## Changelogs

Integrated a basic write implementation for Zarr files with the Polaris FSSpec. Some of the major changes include:
- Added a new endpoint in the client to be able to write a zarr file of a Polaris dataset.
- Added two new methods in the FSSpec: `rm` and `pipe_file`

#### More details of the FSSpec Implementation:
- The `rm` method is currently added as placeholder since it's required for the Zarr writing integration. 
- The `pipe_file` method calls the hub to get a signed URL for a PUT request, then writes the data to the bucket. The S3 bucket uses SHA-256 for data security but it is currently set to None.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08b202d93fbc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.