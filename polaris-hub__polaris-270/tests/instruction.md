# Issue

**Title:** feat: Artifact Versioning - upload benchmark

## Description

## Changelogs

- Added version fields `artifact_version` and `artifact_changelog` to benchmarks
- `upload_benchmark` accepts an optional parameter `parent_artifact_id` (owner/slug), which defaults to None
  - The benchmark will be uploaded as a subsequent version of the provided parent
  - This functionality is different from the previous `upload_as_new_version` param implemented in `feat/artifact-versioning`, and `upload_datasets` has been updated accordingly
- Modified dataset and benchmark `upload_to_hub` functions to also accept `parent_artifact_id`
- Added info about `parent_artifact_id` and uploading new versions of datasets and benchmarks to the documentation
<img src="https://github.com/user-attachments/assets/ee83f0cd-16d8-4e1c-8039-561b1dafd3e3" />
<img src="https://github.com/user-attachments/assets/9e1ac285-d3ac-4bd9-b389-83c6b2b12a00" height="300px" />


---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [ ] _Write concise and explanatory changelogs above._
- [ ] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2cbf6fde8fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.