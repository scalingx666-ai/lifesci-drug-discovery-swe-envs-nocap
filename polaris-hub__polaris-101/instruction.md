# Issue

**Title:** Add "Absolute Average Fold Error" and "Balanced Average Precision" to the metrics

## Description

## Changelogs

- Add metric Balanced average precision from sklearn 
- Add metric Absolute Average Fold Error implementation from https://pubs.acs.org/doi/10.1021/acs.chemrestox.3c00305

---

_Checklist:_

- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `849cae8bffb8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.