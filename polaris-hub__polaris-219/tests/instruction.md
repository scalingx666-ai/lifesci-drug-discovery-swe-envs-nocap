# Issue

**Title:** Chore: Add `imagecodecs` as an optional dependency

## Description

## Changelogs

- Adds `imagecodecs` as an optional dependency.
- Throw an error with an actionable message when a codec is missing.
- Update test cases to use `tmp_path` rather than `tmpdir` ([ref](https://docs.pytest.org/en/stable/how-to/tmp_path.html#the-tmpdir-and-tmpdir-factory-fixtures)).

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Out of curiosity: Are there any design patterns to handle optional dependencies in Python systematically? I did a quick Google search, but couldn't find much. Maybe @jstlaurent knows?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `182f1397d322`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.