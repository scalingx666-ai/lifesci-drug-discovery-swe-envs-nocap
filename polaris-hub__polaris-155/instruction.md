# Issue

**Title:** Updating `base_request_to_hub` method to allow handling of responses without json

## Description

## Changelogs

- Wrapped the JSON parsing of an HTTP response's body in a `try...except` block. This prevents a `JSONDecodeError` in the event the response does not include JSON. This allows the error to still be handled in a meaningful manner. Errors returned from the Hub should be unaffected and output in the same fashion. 

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._ Yes: 
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc93d845f829`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.