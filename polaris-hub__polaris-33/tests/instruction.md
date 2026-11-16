# Issue

**Title:** fix: Local Hub compatibility

## Description

# Description

This PR fixes some issues when running against the Hub locally. There's still some unresolved issues with the Hub on Vercel that I intend to tackle next.

This one moves the pagination to query parameters for list endpoints, which fixes a weird content length issue on the Hub side. It also tightens the Pydantic validation around the various URLs in the settings. There's also a utility function to fully log httpx request/response, to help diagnose issues when errors occur in the library, versus with a CLI request ([httpie](https://httpie.io/) in my case).

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd0c39db5bbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.