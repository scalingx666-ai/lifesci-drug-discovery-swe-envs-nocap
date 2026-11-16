# Issue

**Title:** Pydantic 2.x

## Description

## Changelogs

- Switch to `pydantic >=2.x`.

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

I started converting to pydantic 2.x. It's not that bad but the `root_validator` (now called `model_validator`) logic will need to be refactored a bit.

Some links:

- https://docs.pydantic.dev/latest/migration/
- 
-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `200b5b2d1ed8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.