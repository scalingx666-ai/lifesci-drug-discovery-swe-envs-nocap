# Issue

**Title:** HTML based repr for dataset and benchmark objects

## Description

## Changelogs

- Add a first version of an HTML representation for the Dataset and BenchmarkSpecification objects.

---

_Checklist:_

- [ ] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

For now, this more a prototype to make it nicer displaying the dataset and benchmark objects in a notebook.

I have integrated a small module for `dict2html`. In theory, we can already do that with pandas, but that module can handle nested dict. Maybe we'll drop it, but it allowed me to make a quick prototype (links are not clickable :-()

In short:

![image](https://github.com/datamol-io/polaris/assets/528003/683e702a-290f-4b7e-b0f1-29a0d2691f07)
![image](https://github.com/datamol-io/polaris/assets/528003/7eb3aad8-ff19-45d6-8e68-62dcb8052106)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1db546c0399`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.