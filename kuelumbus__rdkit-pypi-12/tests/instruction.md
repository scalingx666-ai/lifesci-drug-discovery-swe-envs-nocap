# Issue

**Title:** Support building windows wheels (x64)

## Description

* Use cibuildwheel to build windows builds
* Use delvewheels to copy dlls to the wheels
* Clean up

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1e692c24281`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.