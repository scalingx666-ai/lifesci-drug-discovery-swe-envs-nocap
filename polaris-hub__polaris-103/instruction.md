# Issue

**Title:** Competition evaluation

## Description

## Changelogs

Adds support in Polaris client for evaluating competitions. The client runs the same evaluation logic as it does for benchmarks. Competitions differ from regular benchmarks because they have no knowledge of their own test sets (with targets hidden or otherwise). Test data is downloaded by Polaris Hub and passed to the competition evaluation.

API documentation will be done in a separate PR in the context of the rest of the competitions documentation.

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

Competitions use the exact same evaluation logic as regular benchmarks, but with the difference that test labels are passed in separately (rather than accessed from the benchmark/competition dataset). In the case of competitions, the target labels literally do not exist (as opposed to being hidden programatically), and are downloaded on the hub then passed to the evaluation function.

This raises some questions about whether competitions are really as similar to regular benchmarks as we thought they would be, but for now this works and the competition/benchmark distinction can be discussed separately.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26210b2365fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.