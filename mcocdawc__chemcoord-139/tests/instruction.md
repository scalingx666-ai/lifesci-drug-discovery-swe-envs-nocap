# Issue

**Title:** do the getattr overload only at runtime

## Description

do the getattr overload only at runtime
Otherwise non-existent attributes cannot be flagged by mypy.

The attribute access is a convenience for the user, not something for the developer, because it hides to many bugs.

Attribute access to columns
`atom, x, y, z` for Cartesians and
`atom, b, a, d, bond, angle, dihedral` for Zmatrices is still possible.

Added a variable `COORDS: Final = ['x', 'y', 'z']` instead of retyping it all the time.

(added a `.values` `@property` getter similar to the one of a DataFrame)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff3d1302e579`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.