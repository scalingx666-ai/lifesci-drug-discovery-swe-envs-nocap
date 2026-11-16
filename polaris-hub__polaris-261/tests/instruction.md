# Issue

**Title:** Fix: Always pass bytes in the RDKitMolCodec

## Description

## Changelogs

- Always pass bytes to the `VLenBytes` codec, parent class of the `RDKitMolCodec`.

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [X] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

I was running into a Cython issue with a chunk size > 1 because we were passing None rather than bytes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe3bff3652c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.