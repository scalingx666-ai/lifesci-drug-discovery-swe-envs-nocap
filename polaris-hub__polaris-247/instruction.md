# Issue

**Title:** fix: Pin Boto3 version to avoid breaking change

## Description

## Changelogs

- Pin Boto3 to < 1.36.0, to avoid a breaking change in the checksum request headers

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

.

Boto3 has changed its . The header that is now added automatically is not supported by all S3-compatible services, such as Cloudflare R2, which is the backing store for the Polaris Hub storage. The suggested configuration to disable the new behavior does not appear to fix this issue in our case. I've elected to pin the Boto3 version for now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f358bf2e1735`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.