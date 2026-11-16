# Issue

**Title:** Fix bugs and support atom indices as inputs in the lasso viz function

## Description

## Changelogs

- Handle aromatic queries in lasso viz by only preparing the mol for drawing after the matches + add relevant unit test.
- Allow for SMARTS matching in lasso viz function + add unit test.
- Simplify the multiple input types logic in lasso viz.
- Allow to provide a list or list of list of atom indices to highlight in the lasso viz function.
- The lasso viz function will now not throw an error when the `search_molecules` is `None` or empty.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55c190c25644`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.