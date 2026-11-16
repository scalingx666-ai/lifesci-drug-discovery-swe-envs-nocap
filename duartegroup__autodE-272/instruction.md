# Issue

**Title:** Implement DHS and DHS-GS methods

## Description

Implements Dewar-Healy-Stewart method and the hybrid DHS-GS (growing string) method. Optionally run CI-NEB from the end points of converged DHS and DHS-GS method. Also added the base classes for other bracketing methods that could be implemented in future.

Minor changes:
1. Added feature for plotting the energies from a DHS/DHS-GS/other bracketing methods
2. Return a copy instead of new_species from NEB/CI-NEB so that the energy can be read

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6210a14b4ee9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.