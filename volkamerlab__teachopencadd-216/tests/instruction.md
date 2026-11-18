# Issue

**Title:** Fixes for protonation of protein and binding site detection

## Description

## Description
Small fixes for T018 pipeline issues and CI Python 3.9 issues. 

## TODOs
- [x] commands in obabel helper function are run in the wrong order and result in docking to a structure that has no hydrogens
- [x] issue with number of positional arguments when running binding site detection class.
- [x] Under Python 3.9: Check if ´interactions´ variable is dict or a dict embedded in list (Python 3.9) - make sure we work with the dict. See [error message](https://github.com/volkamerlab/teachopencadd/runs/5461111349?check_suite_focus=true#step:8:163).

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81c6562d944e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.