# Issue

**Title:** Use evaluation logic directly in hub, no need for wrapper

## Description

## Changelogs

This PR removes the wrapper around the evaluation logic for use by the hub. Instead we can just call `evaluate_benchmark` directly from there. This requires testing in the context of working competitions, which we will do next. This requires the accompanying PR in the hub, 

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [ ] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6704b6f08e56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.