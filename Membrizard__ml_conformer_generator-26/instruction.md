# Issue

**Title:** feat(js): control bond prediction and final-frame filtering in animateGeneration

## Description

Add predictBonds modes (last/always/never) and optional filterInvalid on the last frame so trajectory viewers can show connectivity forming or treat the final frame like generateConformers output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `210999bfcfa3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.