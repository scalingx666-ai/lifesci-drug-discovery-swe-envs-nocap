# Issue

**Title:** feat: Model Competitions - Model File Upload

## Description

## Changelogs

- Updated `model` class to accept a `file_path` (optional). If `file_path` specified, also calculates new `size` and `md5sum` properties
  - `_validate_file` checks that 1) the file path exists, 2) the file is a `.onnx` file
  - File gets uploaded to r2 using `streaming_set_file()`, which calls the s3 method [`upload_fileobj`](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3/client/upload_fileobj.html)
- Created `InvalidModelError`, used when an invalid `file_path` is passed in to a Model

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c07a41c3409a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.