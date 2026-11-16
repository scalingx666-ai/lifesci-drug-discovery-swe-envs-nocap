# Issue

**Title:** Check to ensure end IDs are greater than start IDs in the PDB reader

## Description

Turns out the fix is really simple. The way to misrepresent PDB files will never cease to amaze me!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c44422ae07d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.