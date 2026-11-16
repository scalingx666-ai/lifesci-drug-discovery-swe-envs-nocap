# Issue

**Title:** End of spin down orbitals section properly detected

## Description

In Orca 6.1.1, the final line ends with 25*'-', it was not detected with the previous definition. It should not affect previous versions (the previous lines are > 25 chars long anyway)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `412d72fb3a3f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.