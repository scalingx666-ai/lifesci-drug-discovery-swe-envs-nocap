# Issue

**Title:** Improve docs and error-handling of the `PolarisHubClient`.

## Description

## Changelogs

- Improved the docstring documentation with regards to the newly added client endpoints.
- Removed validation of the Pydantic model on upload.

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._
  - @hadim Low priority, but should we have a `docs` label?
---

I wasn't sure at first whether to remove the validation on upload. However, the hub will raise an error if anything is wrong and to avoid code duplication, we can simply relay the error message. This might not be the most user-friendly, but manually checking for anything that could be wrong is inefficient on the client side. 

Once users start repeatedly making the same error, we can of course check for that specifically or / and address it in the documentation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82e7db26932d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.