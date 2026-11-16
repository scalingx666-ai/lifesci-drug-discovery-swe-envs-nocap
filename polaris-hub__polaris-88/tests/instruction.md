# Issue

**Title:** Fix "Connection reset by peer" error when uploading large-ish Zarr datasets

## Description

## Changelogs

Fixed the "connection reset by peer" error that was occurring for uploading zarr archives ~ 100MB. This was done by removing the passing of `content` when requesting a signed URL from the Hub.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52573516bb95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.