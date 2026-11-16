# Issue

**Title:** Fix inconsistency between CPU and GPU in LOBPCG

## Description

Remove the `real` conversion in the CPU version of `columnwise_dots`. It is inconsistent with the GPU version and the code prior to #1068. It is also unnecessary, since `real` is already explicitly taken when that matters.

Spotted by @Technici4n

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `668a3be3f0fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.