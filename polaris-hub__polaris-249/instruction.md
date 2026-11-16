# Issue

**Title:** fix: Prevent external AWS configuration from breaking our boto3 config

## Description

## Changelogs

- Explicitly set the region when instantiating a boto3 client, to prevent it from picking one up from some external AWS config

---

_Checklist:_

- [ ]~ _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Boto3 can automatically pick up external configuration for AWS, from various places in the environment: env variables, config files in user directory, etc. This recently caused a problem where it picked up a
region from a user that was not compatible with the Cloudflare R2 bucket we use. Explicitly setting the region when the client is created will avoid this issue in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a96b94bcc23`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.