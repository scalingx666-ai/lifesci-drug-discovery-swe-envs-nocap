# Issue

**Title:** Update GitHub workflow to latest state

## Description

- update `gfortran` and `meson` versions

**NOTE:** The failing `CI / gcc-meson-build (macos-latest, 11)` is due to a failure in the subproject https://github.com/grimme-lab/CPCM-X, detailed .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3d5c5e22ffe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.