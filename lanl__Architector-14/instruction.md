# Issue

**Title:** Ff preopt

## Description

This PR adds the ability to request forcefield preoptimization after the full complexes have been created, but before tight binding relaxation is performed. This option dramatically improves Architector's ability to produce reasonable structures with longer alkyl chains that tend to spatially overlap during generation, but is less high-fidelity and tested than default settings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d5eafbfd9fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.