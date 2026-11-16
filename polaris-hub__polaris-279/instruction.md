# Issue

**Title:** feat: Model Competitions - Competition Model Services

## Description

## Changelogs

- Turned `CompetitionSpecification` into an abstract class, which throws an error if instantiated → must use `PredictionBasedCompetition` or `ModelBasedCompetition` instead
  - These implement `submit_entry` differently (also, users can call `competition.submit_predictions` instead)
  - Replaced all `CompetitionSpecification` instances with `PredictionBasedCompetition` (mostly in tests)
- New function `submit_competition_model` allows users to submit a model to a competition
  - A model artifact id must be passed in, and this gets submitted to the competition
- Updated `submit_to_competition.ipynb` tutorial with instructions for submitting to a model-based competition

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [ ] _Write concise and explanatory changelogs above._
- [ ] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b0bd68c959b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.