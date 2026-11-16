# Issue

**Title:** Symmetry correction for antiferromagnetic ordering

## Description

Correction of symmetries in collinear spin:

Previously, 'symmetry_operations' returned the same symmetries for supercells with equal or opposite magnetic moments on different atoms, which did not allow antiferromagnetic solutions to exist. This behavior comes from 'get_symmetry_with_collinear_spin', which seems to consider only the norm of the magnetic moments.

This PR fixes the issue by discarding symmetries that involve a spin flip (identified by 'get_symmetry_with_site_tensors' but not by 'get_symmetry_with_collinear_spin'). This is a quick fix, these discarded symmetries could maybe be properly taken into account.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4da123756e60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.