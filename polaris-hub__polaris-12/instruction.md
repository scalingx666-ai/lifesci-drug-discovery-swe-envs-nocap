# Issue

**Title:** Simplified the indices for multi-task splits and added the split to the checksum

## Description

## Changelogs

-  by simplifying the multi-task indices from `List[Tuple[int, List[int]]]` to `List[int]` and adds the split to the MD5 checksum of the `BenchmarkSpecification`.

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [X] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [x] _Update the API documentation is a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57fbe44672e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.