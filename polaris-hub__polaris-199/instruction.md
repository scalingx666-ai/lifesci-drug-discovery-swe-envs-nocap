# Issue

**Title:** Add ligand RMSD metrics

## Description

## Changelogs

- Added metric `rmsd_coverage` for docking related benchmarks
- Added unit tests

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---
The rmsd metrics are implemented based on the [Posebuster codebase](https://github.com/maabuu/posebusters/blob/main/posebusters/modules/rmsd.py). A few modifications were made, replacing RDKit callables with equivalent Datamol functions. The RMSD calculation was also simplified to evaluate only the first conformer of the predicted molecule and to consider only heavy atoms.

Note: Posebusters provides a series of checkers, known as '[Posebuster Checkers](https://github.com/maabuu/posebusters/tree/main),' to further filter out unwanted docked ligand conformers. To avoid over-complicating Polaris metrics module with case-specific metrics, users should apply these filters before uploading results to the Polaris hub.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1df9249a7d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.