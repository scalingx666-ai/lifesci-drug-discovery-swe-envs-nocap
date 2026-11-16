# Issue

**Title:** Optimize symmetries_preserving_kgrid for MonkhorstPack

## Description

The previous logic was quadratic in the number of reducible k-points, meaning that we could easily waste **5 minutes** with large k-grids like `[34, 34, 34]`. The new logic is linear in the number of reducible k-points, using the same idea as `symmetries_preserving_rgrid`. 😉

(PS: this should also correctly handle k-grids of size 1 in some directions since the `_check` will trivially pass for them)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff79a5081616`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.