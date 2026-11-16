# Issue

**Title:** The MHFP encoder

## Description

There are couple of changes:

- The implemention of MHFingerprintTransformer itself
- In the previously implemented SECFingerprintTransformer I have changed the name of the encoder field:  "secfp_encoder" -> "mhfp_encoder", it is more consistent with the naming of rdkit
- I have extend the tests, I think all possible,
- All the tests are through, no problem here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a95a3d60876b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.