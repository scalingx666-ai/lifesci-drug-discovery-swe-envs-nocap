# Issue

**Title:** 203 add mol2mol element which only removes solvents if the mol is a mixture

## Description

Implements the `MixtureOnlySolventRemover`.
This object removes the solvents if the molecule consists of multiple fragments.
If the only present fragment is a solvent, it will not be removed.
If only solvent fragments are present, an invalid instance is returned.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `422cc3a5b4aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.