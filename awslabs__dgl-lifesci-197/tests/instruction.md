# Issue

**Title:** unpin scikit-learn version

## Description

It doesn’t matter for you that scikit-learn 1.x doesn’t support Python 3.6 anymore. Their metadata will automatically prevent installation on that Python version.

What does matter is that there’s no reason for you to prevent installation of scikit-learn>=1.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91ef785bb565`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.