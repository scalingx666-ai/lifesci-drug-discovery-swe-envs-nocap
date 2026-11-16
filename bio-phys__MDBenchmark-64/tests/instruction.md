# Issue

**Title:** Update setup.py

## Description

.

Changes made in this pull request:
- Update entries in `setup.py`. Following some examples taken from 

I hope I did not go overboard with the new classifiers and additional keywords, but I don't think more things hurt. Also I sorted the `setup` arguments to the same order as they appear in [the documentation](https://packaging.python.org/tutorials/distributing-packages/#name).


PR Checklist
------------
 - ~[ ] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?~
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bbc7465a8c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.