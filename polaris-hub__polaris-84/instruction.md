# Issue

**Title:** Added the version attribute to the artifact data model

## Description

## Changelogs

- Adds the `version` attribute to the `BaseArtifactModel`. 

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

If we ever want to change a function that would break backwards compatibility, we now have the opportunity to maintain backwards compatibility by adding conditional logic based on the version. Not saying this should be our preferred approach, but I think it's nevertheless good to have the opportunity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3213f7c40443`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.