# Issue

**Title:** Add user_kpoint_settings argument to Distortions.write_vasp_files()

## Description

Allows users to specify `user_kpoint_settings` to override ShakeNBreak's default Γ-only search, alongside two tests for `user_kpoint_settings` and `KSPACING` (in `user_incar_settings`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6dfafa2b321`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.