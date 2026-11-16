# Issue

**Title:** Drop support for Python 3.9

## Description

#222 dropped Python 3.9 from CI, but it did not bump the minimum required Python version.  This PR fixes that.

- [x] Add a release note

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `948e5e1f5913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.