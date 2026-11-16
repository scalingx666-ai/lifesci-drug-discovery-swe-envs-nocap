# Issue

**Title:** Fix ArrayIndexOutOfBoundsException in AtomTools.add3DCoordinates1 for heteroatoms

## Description

### Problem
When `AtomTools.add3DCoordinates1` generates 3D coordinates for unplaced hydrogens attached to a heteroatom (`N`, `O`, `S`), it previously hardcoded `nwanted = 3`. When the reference heteroatom already has 2 neighbor atoms with 3D coordinates (such as a secondary amine `R1-NH-R2` where `nwithCoords = 2`), asking `calculate3DCoordinates2` for `nwanted = 3` is geometrically invalid and returns an empty coordinate array (`new Point3d[0]`). Subsequent attempts to access `newPoints[0]` throw a `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`.

### Solution
- Updated `add3DCoordinates1` to compute `nwanted` as the remaining available tetrahedral coordination slots (`4 - nwithCoords`) for heteroatoms (`N`, `O`, `S`) when `nwithCoords > 0`.
- Added safety bounds check (`j < newPoints.length`) on the coordinate assignment loop to guarantee no out-of-bounds exceptions occur on degenerate or linear geometries.
- Added comprehensive unit test coverage in `AtomToolsTest` validating correct 3D coordinate placement and pyramidal out-of-plane geometry for secondary amines, primary amines, and alcohols.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d222f19aa3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.