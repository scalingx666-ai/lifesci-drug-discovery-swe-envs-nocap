# Issue

**Title:** Allow to terminate reading options with --

## Description

Useful for commandlines like
```
dftd4 --func r2scan --grad -- struc.xyz
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21b828866ed2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.