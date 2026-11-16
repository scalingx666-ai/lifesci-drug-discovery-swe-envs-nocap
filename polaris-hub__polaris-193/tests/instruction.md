# Issue

**Title:** Chore: Add catch-all 'other' category to the generated changelog

## Description

## Changelogs

- Added a `other` category to the changelogs that will include any unlabeled PRs.

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Sometimes we forget to label a PR. This change to the CICD ensures that those PRs still show up in the changelogs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c910f2876ddf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.