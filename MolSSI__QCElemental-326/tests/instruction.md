# Issue

**Title:** Add eigenvalues_and_occupations to wavefunction protocols

## Description

<!-- Thank you for your contribution! -->

## Description
Adds the ability to save only eigenvalues and occupations. Tests have been added.

Background: We need to obtain/store orbital energies for millions of molecules, and we can't afford to also store orbitals for all of them :)

No need to modify QCEngine as the stripping of fields is done in QCElemental.

## Changelog description
Add `eigenvalues_and_occupations` as an option to WavefunctionProtocols

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4a73828790d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.