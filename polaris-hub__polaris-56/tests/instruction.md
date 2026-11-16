# Issue

**Title:** feat: Update result upload endpoint and payload

## Description

# Changelogs

This PR updates the result upload endpoint and the new required payload attributes (`benchmarkArtifactId` and `owner`), introduced in .

It also updates the HubOwner model to the new structure used by the Hub, as well as the related tests.

---

_Checklist:_

- ~[ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- ~[ ] _Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da1976428f26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.