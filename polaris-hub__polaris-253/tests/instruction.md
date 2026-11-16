# Issue

**Title:** chore: Clean up error handling around Hub client requests

## Description

## Changelogs

- Simplify error handling around requests to the Polaris Hub
- Wrap lower-level errors in `PolarisHubError`, to have more helpful messages

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] {_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

I noticed that we had some type incompatibilities when instanciating `PolarisHubError`, around the response object passed in. I corrected this, and took the opportunity to simplify and straighten
up the error handling around the client's requests to the Hub. It should now do a better job at surfacing `PolarisHubError`, which have nicer user facing messages than the underlying errors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41209c6d8e2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.