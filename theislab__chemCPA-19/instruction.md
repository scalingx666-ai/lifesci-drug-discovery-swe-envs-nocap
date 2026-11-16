# Issue

**Title:** GPU Evaluation

## Description

Related to #17 

Main change: Evaluation (R2Score) now runs on the GPU instead of on the CPU. I couldn't test it on LINCS (preprocessing takes too much time), but on SciPlex3 it now takes 3min instead of 12min to evaluate.

There is some code in them `simon/` folder that we can delete before we Open-Source, it think it's fine to commit it for now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b0718c31449`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.