# Issue

**Title:** feat: Model Versioning

## Description

🗝️ 

## Changelogs

- Added `artifact_version` and `artifact_version` fields to model artifact
- Modified `upload_to_hub` and `upload_model` functions to accept `parent_artifact_id`, in order to upload a new version of a model
- Updated tutorial to explain how to upload a new version of a model

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4079dafd6c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.