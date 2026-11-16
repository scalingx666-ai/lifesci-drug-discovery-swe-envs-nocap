# Issue

**Title:** feat: Add an optional username/password login mode

## Description

## Changelogs

- Add optional settings for username and password
- Update token fetching from the Hub to use username/password when present

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---
When present, the Polaris Hub client will use the configured `POLARIS_USERNAME` and `POLARIS_PASSWORD` environment variables for authentication to the Hub, rather than an interactive login flow involving a browser session. This will only work for Polaris Hub users that have set a password on their account. The username is one of the email addresses associated with the Polaris Hub account.

This PR depends on a , to enable the OAuth Resource Owner Password Credentials Grant.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90fce00e3f1c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.