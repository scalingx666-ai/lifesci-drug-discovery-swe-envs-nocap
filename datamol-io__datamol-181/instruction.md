# Issue

**Title:** Lazy loading

## Description

Checklist:

- [ ] Was this PR discussed in a issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR. 
- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [ ] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

This is an attempt to dramatically reduce datamol import time. The approach has been inspired (if not completely copy/pasted) from openff-toolkit (https://github.com/openforcefield/openff-toolkit/blob/b52879569a0344878c40248ceb3bd0f90348076a/openff/toolkit/__init__.py#L44).

On my laptop, it reduces the import time from 950 ms to 5 ms. Subsequent call to datamol functions do not seem slow (more tests needed here).

Lazy loading is only a first optimization to be done. Another one that could be tackled independently of this PR is to review and refactor the datamol submodules. For example, `.mol` depends on `.convert` and `.convert` also depends on `.mol`. Ideally, a sane tree hierarchy should be defined.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34a79e701821`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.