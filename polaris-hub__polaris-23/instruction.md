# Issue

**Title:** Add code coverage

## Description

## Changelogs

- Add code coverage during testing. Tests will fail if coverage is under 78% at the moment.
- switch from `class Config` to `model_config` (see https://docs.pydantic.dev/dev-v2/migration/#changes-to-config)

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

We should try to aim for >90% since it's always easier to do that early during the course of a project.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82adf80d1d21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.