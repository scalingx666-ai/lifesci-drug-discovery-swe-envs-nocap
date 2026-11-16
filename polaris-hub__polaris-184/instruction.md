# Issue

**Title:** Fix/column annotation

## Description

## Changelogs

- Add validator and serializer for `content_type` class
- Specified `content_type` to `PDB` in `pdb_converter`.

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [ ] _Write concise and explanatory changelogs above._
- [ ] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

A minor PR to fix the dataset.table visualization and serialization for dataset `content_type` attribute.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d467f56cf296`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.