# Issue

**Title:** fix: Better handling when no cached token exists, with more decriptive error

## Description

## Changelogs

- Make sure the `ensure_active_token` methods will identify that there is no token
- Surface a better error message when it happens, so users can take action to remediate

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Adresses #251

This bug fix will better handle cases where the OAuth token is `None`. This might result from a new user that has not logged in, tokens that were not cached, or cached credentials that have
expired. When the client is used in the loader functions, and one such situation occurs, ane exception will be raised that includes a better, actionable error message for the user.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1649472ec5ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.