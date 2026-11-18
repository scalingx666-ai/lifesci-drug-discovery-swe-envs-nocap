# Issue

**Title:** Python requirements >= 3.8

## Description

## Description
Bump up our Python requirements to Python 3.8 (i.e. dropping support for 3.7).
See discussion here: 

## Todos
- [x] Pin Python>=3.8 and `biotite`>=0.34.0 in [environment file](https://github.com/volkamerlab/teachopencadd/blob/master/devtools/test_env.yml)
- [x] Update [CI](https://github.com/volkamerlab/teachopencadd/blob/master/.github/workflows/ci.yml) and [docs](https://github.com/volkamerlab/teachopencadd/blob/master/.github/workflows/docs.yml) workflows(move from 3.7 to 3.8)
- [x] Unpin `h5py` (not needed anymore) --- Note: Later even dropped explicit install: 

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31f5a264c935`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.