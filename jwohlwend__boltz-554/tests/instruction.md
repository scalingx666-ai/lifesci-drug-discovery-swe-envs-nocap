# Issue

**Title:** Fix bf16 dropout

## Description

- Ensures rand is evaluated in fp32.
- Changes inequality to reflect [0,1) rand interval.
Fixes unexpected msa dropout due to bfloat16 datatype.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee96012a0ccf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.