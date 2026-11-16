# Issue

**Title:** Fix dftd4 tests by updating to more recent version

## Description

Take more recent `dftd4` version to prevent tests from failing.
```
[wrap-git]
directory = dftd4
url = https://github.com/dftd4/dftd4
revision = v3.6.0
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42d6c80f1e6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.