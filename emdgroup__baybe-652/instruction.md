# Issue

**Title:** Mismatch Targets

## Description

Implements #631

Here the resulting transformations based on different objectives:

Standard Match Targets, `match_value=1` (for reference)
<img width="628" height="452" alt="image" src="https://github.com/user-attachments/assets/862cc260-b8cc-4525-b090-9f1070501a11" />

Mismatch Targets (seen by a `SingleTargetObjective` or `ParetoObjective`)
<img width="621" height="452" alt="image" src="https://github.com/user-attachments/assets/ac3c2547-fdab-4e9b-bbaf-7437dbc332cf" />

Mismatch Targets (seen by a `DesirabilityObjective(`require_normalization=False`)`)
<img width="613" height="459" alt="image" src="https://github.com/user-attachments/assets/d5c4aa8e-bc94-4fd3-861a-20595198f74b" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48046272ca84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.