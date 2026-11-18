# Issue

**Title:** Fragment generation improvs

## Description

- Added intermediate alignment of generated fragments to principal inertial frame during IFM
- Added transformation of the fragment in the same way as reference for consistency (generate_conformers)
- Added additional demo files
- Implemented improvements for ONNX version

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6bcd163e1da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.