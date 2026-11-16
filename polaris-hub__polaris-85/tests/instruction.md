# Issue

**Title:** Fix a bug in Dataset.cache() and set a default timeout for the PolarisHubClient

## Description

## Changelogs

- After calling `Dataset.cache()` the `zarr_root` wasn't reset, because of which it was still using the remote archive. 
- The `default_timeout` parameter for the `PolarisHubClient` can be passed to the `httpx.Client` to properly set it as the default

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92ddf52b8b03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.