# Issue

**Title:** Fix sumo-phonon-bandplot bug for band.yaml plotting

## Description

One or two misplaced lines of code (e.g. poscar = Poscar.from_file(poscar) missed because it was in a separate if statement) which meant that plotting from a pre-generated `band.yaml` file (whether from sumo or phonopy) didn't work.
Tested and seems to fix the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e72fbbfe72c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.