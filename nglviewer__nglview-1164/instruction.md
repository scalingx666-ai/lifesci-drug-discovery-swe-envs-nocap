# Issue

**Title:** chore: use jupyter_packaging>=0.12.2 for Python 3.13+ and fix broken CI

## Description

If `__init__.py` discards `importlib.metadata`, it would have an unexpected side-effect. For example, I put the link that NumPy testing library also uses `importlib.metadata` to fail.

🔗.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d71919f7ba3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.