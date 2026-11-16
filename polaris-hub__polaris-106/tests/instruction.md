# Issue

**Title:** feat: Update settings for production environment

## Description

## Changelogs

This PR updates the default settings for the client to use the new Clerk production environment.

For local dev, the client now supports using a `.env` file to point to Clerk's development environment. Use these values:
```.env
POLARIS_HUB_URL="http://localhost:3000/"
POLARIS_AUTHORIZE_URL="https://pure-whippet-77.clerk.accounts.dev/oauth/authorize"
POLARIS_TOKEN_FETCH_URL="https://pure-whippet-77.clerk.accounts.dev/oauth/token"
POLARIS_USER_INFO_URL="https://pure-whippet-77.clerk.accounts.dev/oauth/userinfo"
POLARIS_CLIENT_ID="QJg8zadGwjnr6nbN"
```

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f7d6ec650db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.