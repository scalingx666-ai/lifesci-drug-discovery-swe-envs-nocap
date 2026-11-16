# Issue

**Title:** Implement EEQ model for charges and atom-resolved energies

## Description

Try it out with

```
pytest --pyargs xtbml.charges --doctest-modules
pytest test/test_charges
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99d9f3640096`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.