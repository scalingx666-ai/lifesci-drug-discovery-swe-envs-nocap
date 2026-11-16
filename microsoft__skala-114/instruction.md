# Issue

**Title:** trying to fix doctest with fixture as well

## Description

The problem was that doctests and normal tests should all the see the fixture. So we have to put it in root.

Now everything should see the fixture and it should be fine. A long term solution will be to restructure the repo, so that the model and the pyscf plugin are separate folders with their respective tests. Then the pyscf plugin has its own conftest at root and everything will be nicer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e348641a3a35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.