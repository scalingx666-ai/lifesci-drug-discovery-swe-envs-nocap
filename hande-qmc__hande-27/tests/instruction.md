# Issue

**Title:** CPP definitions can be passed from configuration

## Description

Additional CPP definitions can be passed from configuration with:
`./cmakeconfig.py --add-definitions="-DTHIS -DTHAT -DTHAT_ONE_TOO"`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9524defe2869`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.