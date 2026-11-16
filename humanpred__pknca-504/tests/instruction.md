# Issue

**Title:** Exclude message for flat concentrations in half.life calculation

## Description

The PR handles the half-life calculation cases where all concentration values are identical (i.e., flat data), which makes half-life computation mathematically impossible. It also adds a corresponding unit test to ensure this scenario is properly excluded and reported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f102130159a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.