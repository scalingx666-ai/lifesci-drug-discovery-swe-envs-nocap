# Issue

**Title:** Fix zmat file printout (bond length conversion from Bohr to Ang)

## Description

zmat file contained bond lengths in Bohrs, hence broken structures when opening with Molden. 
Plus, enabled -zsort only run (did not work for me before)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5b749f85032`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.