# Issue

**Title:** Fix use python3 instead of python2 to run hello.py

## Description

`qpsh` should now use `python3` to run `hellow.py`, not `python2`. This causes an unnecessary dependency on `python2`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b32fc67ac55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.