# Issue

**Title:** Allow different conformer connectivity

## Description

This PR adds an `allow_connectivity_changes` keyword argument to `autode.species.Species.find_lowest_energy_conformer`, which if set to True skips discarding conformers based on differing molecular graphs (connectivity). This is required if, for example, there are 'dative' bonds that can be formed between the constituent parts of a complex. For example, [Na{H2O)3]+  will not generate any valid conformers if initialised from H2O and Na+.

- Adds functionality
- Adds test
- Adds to NCI documentation

Thanks @kjelljorner for the suggestion

- [x] Add conformer prune on connectivity
- [x] Self review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee99ab85e386`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.