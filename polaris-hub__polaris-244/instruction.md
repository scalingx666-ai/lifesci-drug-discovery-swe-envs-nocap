# Issue

**Title:** chore: Improve data loading performance in S3 store

## Description

## Changelogs

- Add a LRU cache to the `S3Store` class, to cache fetched objects
- Add chunk-based iterators, to improve performance when traversing dataset columns

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

This builds on the work Cas did in `feat/optimize-dataloader`. I increased the number of cached objects in the S3 store, since most of them are small anyway. I also added a Generator-based chunking iterator, that I think is simpler than the class-based approach. It should reduce the amount of decompression that takes place when iterating through a dataset row-by-row.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ffca9da4d8e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.