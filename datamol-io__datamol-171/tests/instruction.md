# Issue

**Title:** New doc branding

## Description

Checklist:

- [ ] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [ ] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b5a4d9b52fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.