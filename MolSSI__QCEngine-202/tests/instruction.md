# Issue

**Title:** Entos wavefunction properties

## Description

<!-- Thank you for your contribution! -->

## Description
Support for wavefunction properties has been added for the entos Harness. One thing of note is that the basis set information does not exactly match the one found on basis set exchange for the same basis (e.g. def2-svp for Oxygen). I believe this is due to entos returning the normalized primitives in its output. 
- [x] No based on QCER discussion. ~~Should the normalized primitive information be included in the `extras` field?~~
- [x] Do quantities like the Fock and density matrices need to follow CCA spherical/cartesian basis ordering (for p functions and above)? 

## Changelog description
Support for wavefunction properties has been added for the entos Harness.

## Status
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcd6f3ddc43a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.