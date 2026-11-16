# Issue

**Title:** Add compression of QByteArrays

## Description

Trivial code change, no major performance hits, massive reduction in file size....should have done this a while ago.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b70a72ee30b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.