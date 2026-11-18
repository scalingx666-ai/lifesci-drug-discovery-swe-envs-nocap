# Issue

**Title:** T000 - Talktorial template

## Description

## Details

- Talktorial ID: T000
- Title: Talktorial template
- Original authors: @dominiquesydow 
- Reviewer(s): @AndreaVolkamer 
- Date of review: 15.12.2020

## TODO

Update template w.r.t. @AndreaVolkamer's suggestions (that she send via PM - copied here):

- [x] (it is self-explanatory, but one could add a note at the beginning that examples are taken from T001)
- [x] Practical: Short summay -> Short summary
- [x] In the path description make it even more explicit, that no relative paths should be given 
- [x] Info for imports (copy info on ordering from issue (?))
- [x] maybe for later: generally we could add some general tips from the PR description in here, I will list a few here
  - [ ] Style guides black, Pep8, …
  - [x] If functions are used, use docstrings, copy one example over? (one more comment on fcts (local/global variables - do not use globals in function) + link to docstring documentation
  - [x] Or tips at the end: 
    - Clear output and rerun, does it finish without errors?
    - Deterministic behavior/output? (help with CI comments)
    - Check runtime?
- [x] In talktorial practical header repeat once that one should make sure the titles are the same as above (as well as the indentation)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e99614c65b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.