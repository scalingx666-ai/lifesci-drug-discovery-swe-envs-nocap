# Issue

**Title:** FIx for show_pdbid and Python3

## Description

My simple test notebook with show_pdbid("3pqr") does not work for Python 3.7.1 in anaconda-2018.12
Nothing gets displayed.  FIxed it by decoding the bytestring returned from urlopen()

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d22bcff8d2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.