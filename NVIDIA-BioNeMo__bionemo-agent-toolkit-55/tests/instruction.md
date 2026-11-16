# Issue

**Title:** Sign genomics-workflow-acceleration

## Description

Point the workflow readiness reference to the Bash Parabricks helper in both the source and generated skill, and remove obsolete source metadata.

Extracted only the genomics-workflow-acceleration changes from parabricks-skill commit ddee3312cc7875cd7ceecd0dadc042fc25bdefd6. The referenced Bash helper is introduced by the separate Parabricks PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3665dfba6893`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.