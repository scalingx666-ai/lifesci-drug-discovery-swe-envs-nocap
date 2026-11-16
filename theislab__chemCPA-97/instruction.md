# Issue

**Title:** Separate adversary regularisation and make eval modular

## Description

This PR improves two things: 

- Add a separate covariate regularisation parameter
- Make the evaluation computation modular

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a57919238a1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.