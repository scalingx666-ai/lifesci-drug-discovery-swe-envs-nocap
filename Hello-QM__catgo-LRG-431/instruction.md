# Issue

**Title:** Bond Disappear Problem Fixed

## Description

## Summary

Fixes a bug where bonds disappeared after adding a periodic lattice to a non-periodic molecule through **Build Tools > Lattice**.

## What changed

- Fixed the GUI lattice-creation path for molecules without an existing cell.
- Preserved Cartesian atom positions while correctly recomputing fractional coordinates (`abc`) after the molecule is moved into the new periodic box.
- Reused a shared lattice-wrapping helper instead of keeping coordinate-conversion logic inside the UI component.
- Added regression tests for H2O in both orthogonal and non-orthogonal boxes.

## Why

Previously, the GUI path wrote shifted Cartesian coordinates into both `xyz` and `abc`. After a lattice was added, `abc` should represent fractional coordinates. Because bond detection uses fractional coordinates for periodic/minimum-image logic, molecules such as H2O could appear as disconnected atoms after creating a box.

The CatBot/backend path already behaved correctly because pymatgen generated proper fractional coordinates.

## Validation

- Added tests confirming:
  - `abc` correctly converts back to `xyz`
  - molecular bond lengths are preserved after wrapping in a periodic box
  - minimum-image distances remain correct
  - non-orthogonal lattice boxes are handled correctly

Tested with:

```bash
node_modules\.bin\vitest.cmd run tests/vitest/structure/lattice-ops.test.ts tests/vitest/atom-graph.test.ts tests/vitest/structure/bonding.test.ts

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4216160c24ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.