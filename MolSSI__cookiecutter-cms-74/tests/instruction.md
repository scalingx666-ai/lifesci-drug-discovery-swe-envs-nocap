# Issue

**Title:** remove conda recipe. allow `python setup.py test` to run correctly

## Description

* removed the conda recipe b/c (a) I don't think it gets much populated by the cookiecutter, (b) isn't used in CI, and (c) makes a _third_ place ppl need to specify deps and versions
* some changes that allow pytest via `python setup.py test`. see MolSSI/QCElemental#39

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `054521d78886`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.