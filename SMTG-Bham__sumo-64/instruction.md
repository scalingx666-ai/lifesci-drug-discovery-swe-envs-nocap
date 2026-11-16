# Issue

**Title:** Restrict Pymatgen version for Python 3.5 installation

## Description

This should solve #62 by restricting the range of installed Pymatgen versions when installing Sumo under 3.5. We should do at least one point-release with this in place before dropping 3.5 support ourselves so that 3.5 users have a known working Sumo installer. We will however need to drop 3.5 when we use any new Pymatgen features.

Once this is in master I suggest that other pull requests rebase and force-push in order to get their CI working without adding a lot of merges to the history.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4b6da085f0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.