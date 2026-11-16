# Issue

**Title:** Fix NNP (a.k.a. QMML)

## Description

- [x] Rename QMML to NNP
- [x] Fix NNP configuration
  - [x] Factor out `_get_queue`
  - [x] Split _get_reference_calculator into `_get_qm_calculator` and `_get_nnp_calculator`
- [x] Simplify parameter directory

~~Depend on #815~~
Depend on

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f161f5cbac1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.