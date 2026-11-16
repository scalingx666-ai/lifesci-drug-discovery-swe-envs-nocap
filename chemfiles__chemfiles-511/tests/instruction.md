# Issue

**Title:** Read and write forces in Gromacs TRR files

## Description

.

This reads forces from a TRR trajectory, converts them from `kJ / (mol * nm)` to `kJ / (mol * Angstrom)`, and stores them in the atomic property `force`.
When writing, the conversion is done in reverse. For atoms without the atomic property set, a default value of zero force is written (should there be an error / warning?).

Additionally, some smaller changes:
- update Readme to reflect changes from #480.
- fix comparison in an C example.
- run `clang-format` and ICWYU on the TRR related files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b7066189063`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.