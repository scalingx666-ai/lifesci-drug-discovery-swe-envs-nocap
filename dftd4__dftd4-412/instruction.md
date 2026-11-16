# Issue

**Title:** Keep PySCF dispersion molecules consistent during reset

## Description

PySCF energy and gradient scanners require the dispersion correction to track molecule changes. The existing reset hook could instead clear the dispersion molecule when called without an argument.

- **Reset handling:** Preserve the current molecule when omitted; skip the dispersion reset when `with_dftd4` is disabled.
- **Regression coverage:** Check molecule synchronization and scanner results across geometry changes for energy and gradient wrappers with D4 and D4S.

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff5a83006f08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.