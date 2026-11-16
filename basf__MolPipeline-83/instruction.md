# Issue

**Title:** mol2morgan_fingerprint: remove deprecated fp function

## Description

Fixes 

    
- Remove AllChem.GetMorganFingerprintAsBitVect
  from the code because it is deprecated.
- Add a test to ensure the bit2atom mapping works
  as intended.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f3d5213280b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.