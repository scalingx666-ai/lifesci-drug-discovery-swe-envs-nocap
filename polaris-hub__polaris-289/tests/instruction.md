# Issue

**Title:** refactor/chore: Removing dataset/benchmark upload functions from Python client

## Description

## Changelogs

This PR removes the ability to upload datasets and benchmarks directly from the Python client.

- Changed `upload_to_hub` functions in `client.py` to raise a `PolarisDeprecationError`.
- Kept artifact-specific `upload_to_hub` functions.
- Removed documentation regarding dataset/benchmark upload functionality.

<details>
<summary>Outdated</summary>

- Removed from `polaris/hub/client.py`:
  - `upload_dataset` method
  - `_upload_v1_dataset` helper method
  - `_upload_v2_dataset` helper method
  - `upload_benchmark` method
  - `_upload_v1_benchmark` helper method
  - `_upload_v2_benchmark` helper method
- Removed from `polaris/dataset/_base.py`:
  - Abstract method declaration for `upload_to_hub`
- Removed documentation regarding dataset/benchmark upload functionality.

</details>
---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59f879385d5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.