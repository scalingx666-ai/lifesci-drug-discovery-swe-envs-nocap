# Issue

**Title:** Chore: Remove duplicate and unused CompetitionPredictions class

## Description

## Changelogs

- Removed the duplicate `CompetitionPredictions` class

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

We use [`polaris.evaluate._predictions.CompetitionPredictions`](https://github.com/polaris-hub/polaris/blob/main/polaris/evaluate/_predictions.py#L252), we also had [`polaris.evaluate._results.CompetitionPredictions`](https://github.com/polaris-hub/polaris/blob/main/polaris/evaluate/_results.py#L202). Since the latter wasn't used, I deleted it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66fb428d4824`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.