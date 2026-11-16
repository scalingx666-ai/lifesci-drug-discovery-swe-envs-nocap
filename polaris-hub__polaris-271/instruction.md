# Issue

**Title:** Client: Model artifact remaining changes

## Description

## Changelogs

- **New Features:**
  - Added `list_models` utility function.
  - Introduced a **"Create a Model"** tutorial.
  - Added `model_artifact_id` as a computed property in `ResultsMetadataV2`.
  
- **Improvements:**
  - Added `code_url` as an alias for `github_url` in `ResultsMetadataV1`.
  - Added `report_url` as an alias for `paper_url` in `ResultsMetadataV1`.
 
- **Bug Fixes:**
  - Fixed a bug in result evaluation by using a shallow copy of subsets instead of a deep copy.
  - Fixed a bug in the `get_model` method (wrong endpoint URL).
  - Fixed a bug in the `_get_v2_benchmark` method (`TypeError: got multiple values for keyword argument 'split'`)
  - Fixed typings in the `upload_results` method for `results` param.
  - Corrected small typos in docstrings.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

## Demo Videos

<details>
<summary><b>Model Landing and Detail Pages / Leaderboard</b></summary>

https://github.com/user-attachments/assets/de858c5f-56f0-46c4-b07d-61a192b5ca4b
</details>

<details>
<summary><b>Create a Model</b></summary>

https://github.com/user-attachments/assets/7443bb50-87b5-4cdb-88ff-d9647771a84b
</details>

<details>
<summary><b>Attach a Model to results</b></summary>

https://github.com/user-attachments/assets/6ccd92cc-8de3-4199-9a18-80860b8487c9
</details>

<details>
<summary><b>List models/Load a specific Model</b></summary>

https://github.com/user-attachments/assets/6247e470-1f82-4bd3-a10b-686c1a0253a1
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8196bebb846`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.