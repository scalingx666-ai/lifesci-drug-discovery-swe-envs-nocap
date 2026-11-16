# Issue

**Title:** Add fp transformers

## Description

Added additional transformers mol to fingerprint (MACCS, atom pairs, topological torsions, rdkitfp).
Still need to test the functions and the options.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `778fde7a352a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.