# Issue

**Title:** Support OpenFF Toolkit v0.11+ in openmm.py

## Description

Hi! This is my first contribution here, let me know if I've done anything wrong!

## Description

The OpenFF Toolkit v0.11 includes breaking changes, including enforcing that conformer units are specified with the new OpenFF Units package rather than OpenMM units. This PR updates QCEngine to be compatible with the new version while preserving compatibility with the old versions.

## Changelog description

Support OpenFF Toolkit v0.11+

## Status

<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2793f5853ecc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.