# Issue

**Title:** Optimize the data loader for datasets that fit in memory or on a local disk

## Description

## Changelogs

- Added `Dataset.load_in_memory()`, which optimizes how a Zarr archive is stored _if_ it fits in main memory.
- Added a new tutorial to highlight the effect of this function and to give general optimization tips.
- Changed from `df.loc[row, col]` to `df.at[row, col]` to optimize Pandas indexing. 
- Use memory mapping to load data locally.
- Use a default chunk size of 1 in the `SDFConverter` to have a chunk per data point. 

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

The changes in this PR were the results of some iterative profiling and optimization that was documented [here](https://docs.google.com/document/d/1Ed1rEkPja0OpRujocJbxHej0jep_3Erya6IelsgS7pw/edit?usp=sharing) and [here](https://docs.google.com/document/d/1gP-usLiLG7hqg-M0zE0n1KHFl7o6Z-1fIhsOok5NLjw/edit?usp=sharing).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e4cdaa71095`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.