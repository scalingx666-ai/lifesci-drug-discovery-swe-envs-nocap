# Issue

**Title:** Fix: `PolarisFileSystem` uses the dataset name instead of the dataset slug, causing a 404

## Description

## Changelogs
- Sluggify the dataset name in the `PolarisFileSystem`.
- Serialize the `cache_dir` to a string.
- Updated Zarr dataset tutorial to reflect recent changes.
---

_Checklist:_

<s> - [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._ </s>
<s>- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._</s>
<s>- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._</s>
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

When uploading the dataset, the dataset slug has to be used to get the correct path to the R2 bucket. Otherwise, the Hub returns a `404`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5cf6092615a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.