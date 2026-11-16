# Issue

**Title:** Redid the `BenchmarkResults` structure to be tabular

## Description

## Changelogs

- Updated to `BenchmarksResults.results` field to be of a tabular format. .
- Added convenience methods to each of the artifacts to upload it to the hub. They are all light wrappers around the client's methods.
- Add consistent, more informative error messages when the user is not logged in.

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---
Results now look like this :point_down: 

| Test set | Target label | Metric | Score |
| -------- | ------------ | ------ | ----- |
| test_iid | EGFR_WT      | AUC    | 0.9   |
| test_ood | EGFR_WT      | AUC    | 0.75  |
|    ...   |      ...     |  ...   |  ...  |
| test_ood | EGFR_L858R   | AUC    | 0.79  |

I thought about the results data-structure for these last few days, but couldn't come up with anything more convenient than a tabular Pandas DataFrame. Let's see how far that gets us! :slightly_smiling_face:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d2a92656a54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.