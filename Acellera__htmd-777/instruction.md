# Issue

**Title:** Fix PRM writer for CGENFF

## Description

#776 

It was an issue where I didn't update the PRM writer when I made the `getParameters` function for the new parmed versions and it went unnoticed.

Since I was making changes I also made parameterize only print equivalents when they exist, instead of printing a list of all atoms of the molecule which is useless.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31bb53fa45f4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.