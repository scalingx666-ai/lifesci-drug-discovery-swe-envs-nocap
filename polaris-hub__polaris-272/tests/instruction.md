# Issue

**Title:** feat: Artifact Versioning

## Description

## Changelogs

⭐ 

- **Artifact Model:**
  - Added version fields `artifact_version` and `artifact_changelog` to datasets and benchmarks
  - Created a slug `field_validator` to accept a slug from the Hub (if passed), otherwise `slugify`s the name
  - Modified the `urn_for` method to use a new function `build_urn` 
- **Uploading new versions**: `parent_artifact_id` (owner/slug) can be specified in dataset/benchmark `upload_to_hub`, `upload_dataset`, or `upload_benchmark` functions
  - This will attempt to upload the new artifact as the direct child of the parent
- **Name → Slug:** Replaced many instances of `name` with `slug` (e.g. in `get_artifact`, etc)
- **Documentation:** Wrote docstrings explaining `artifact_version`, `artifact_changelog`, and `parent_artifact_id`. Also mentioned how to upload a new version (at the end of Create a Dataset and Create a Benchmark tutorials)
  <details>
    <summary>Preview</summary>
    <img src="https://github.com/user-attachments/assets/ee83f0cd-16d8-4e1c-8039-561b1dafd3e3" />
    <img src="https://github.com/user-attachments/assets/9e1ac285-d3ac-4bd9-b389-83c6b2b12a00" height="300px" />
</details>


---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b98b741e734f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.