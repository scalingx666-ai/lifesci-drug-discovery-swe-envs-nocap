# Issue

**Title:** Fix TRIC bugs and add improper dihedrals for planar centers

## Description

This addresses issue #32.

TRIC (Translation-Rotation Internal Coordinates) fixes:
- Fix line ordering in find_all_bonds(): move labels[nbonds == 0] = -1 before the allow_fragments break to prevent rotation ICs from being incorrectly added to single-atom fragments
- Add scale parameter to find_all_bonds() (default 1.25) so users can configure the bond detection threshold
- Update validate_basis() to correctly calculate expected DOF when TRICs are present (3N instead of 3N-6)

Improper dihedral detection for ODE convergence:
- Add automatic detection of atoms with 3-4 neighbors that don't have proper dihedrals passing through them
- Create improper dihedrals to capture the out-of-plane (umbrella) mode
- This fixes the "Geometry update ODE is taking too long to converge" error that occurred with ill-conditioned Jacobians at planar geometries
- For tetrahedral geometries (e.g., CH4), the improper is redundant but harmless - the pseudo-inverse handles the extra coordinate gracefully

Add TRIC tests for single-atom fragments, scale parameter, and DOF validation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f8b21d67700`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.