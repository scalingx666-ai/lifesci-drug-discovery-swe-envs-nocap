# Issue

**Title:** Improve meta-GGA stability in SCF

## Description

Mixes not in (ρ, τ) but in (ρ, τ - τW) with τW the von Weizsäcker kinetic energy.

- [x] Small test

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38d2c2e906f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.