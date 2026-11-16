# Issue

**Title:** Force the user to alias >4-letter residue names

## Description

Sometimes i.e. when building membranes you might end up having very long resnames. For example SAPI24 lipids.

The build process needs to write out PDB files, so the resnames get truncated and you get a big bad mess where SAPI24 becomes SAPI which is a different residue in CHARMM etc. 

So here we force the user to alias any resname with more than 4 letters

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2f979d98adc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.