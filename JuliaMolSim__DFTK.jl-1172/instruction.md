# Issue

**Title:** Automate `elastic_constants` by AD-DFPT as a postprocessing

## Description

Following up on the ideas at #1162.

This PR aims to automate the clamped-ion elastic constants as a convenient postprocessing function `elastic_constants(scfres)` for 1) the generic case of not using symmetry (most expensive, 6xDFPT on a fully unfolded kgrid...), 2.1) the most common case of cubic crystals (least expensive, 1xDFPT on a partially unfolded kgrid). Optimizations for other the point groups could be implemented later following a similar pattern.

progress:
- [x] Implement generic case
- [x] Implement cubic case
- [x] use SCF results from scfres and partially unfold (#1308; Update: just warm-starting with the correct density and tightened diagonalization tolerance)
- [x] more testing
- [x] mention in elastic constants docs example

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9f353b10239`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.