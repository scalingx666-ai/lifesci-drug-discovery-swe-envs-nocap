# Issue

**Title:** Reaction

## Description

This PR brings back the reactions module. 
The reactions/_reactions.py simplified `apply_reactions` and `compute_reaction_product`.
The reactions/_attachments.py is for attachment point manipulation.

Checklist:

- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [x] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._
- [x] Add tutorial.

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81aed56746fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.