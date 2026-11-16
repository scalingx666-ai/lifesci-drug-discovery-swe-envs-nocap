# Issue

**Title:** Remove the curation module and update branding

## Description

## Changelogs

- Removed the curation module from Polaris. This code now lives in a separate package called [Auroris](https://github.com/polaris-hub/auroris).
- Updated the branding.

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28868d31a5c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.