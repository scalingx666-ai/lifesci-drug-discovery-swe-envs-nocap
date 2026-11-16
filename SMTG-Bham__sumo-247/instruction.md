# Issue

**Title:** Fix import from Castep lattice_abc format

## Description

Cell files with lattice_abc vectors were broken, and this was not causing test failures because it wasn't tested. Here we:

- Create test files with and without explicit dimension units
- fix the treatment of lattice_abc data in "two-rows" format (no unit)
- support recent versions of Pymatgen by migrating to
- Lattice.from_parameters from the deprecated Lattice.from_lengths_and_angles
- Note that Lattice.from_parameters does not produce the same cell matrices as CASTEP, and raise a warning if the user has `abs_positions`. The positions will very likely be wrong in this case; but not many features of Sumo are impacted, so perhaps it would be overkill to error out entirely.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99f2a4d64acb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.