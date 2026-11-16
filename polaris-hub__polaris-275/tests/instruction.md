# Issue

**Title:** fix: Extras are not recognized and installed

## Description

## Changelogs

- Add a `project.optional-dependencies` to the `pyproject.toml` file

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

Adresses #274

Using the [PEP 735](https://peps.python.org/pep-0735/) to define dependency groups means they are not recognized as extras when Polaris is specified as a dependency. So doing `pip install
polaris-lib[codecs]` will not also install `imagecodecs` as a dependency.

We probably have not noticied this behavior when developping the library locally because `uv sync` recognizes the dependency groups.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fd156b52102`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.