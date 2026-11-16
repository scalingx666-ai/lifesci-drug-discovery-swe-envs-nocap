# Issue

**Title:** Rewrite dm.viz.circle_grid with RDKit's canvas and support grid image for lasso highlight

## Description

## Changelogs

- Add supports for molecular grid in lasso highlight, fixing #199 
- Rewrite circle grid with the RDKit canvas system and remove image stacking, fixing #196 
- Allow more functionalities in `dm.circle_grid` (better management of molecule size, more drawing options exposed to the user, support of some of the key features of `to_image` including align and atom/bond highlight
- Minor refactoring of the viz module, with a new `image_to_file` function
---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [x] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

This PR  and #199

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bea9401c8d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.