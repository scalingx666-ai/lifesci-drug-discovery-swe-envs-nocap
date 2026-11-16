# Issue

**Title:** Atomic grid refactorization update

## Description

1. Rename AtomicGrid -> AtomGrid
2. Rename special_init -> from_pruned, quick_init -> from_predefined
3. Merge several one-line functions into other low-level private function
4. Set default center to None
5. Rename property rad_grid -> rgrid
6. Merge convert_points_to_sph to convert_cart_to_sph

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bebef397362`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.