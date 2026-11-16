# Issue

**Title:** xtb: fix qcg and docking crash with crest

## Description

Fixes crashes in xTB's docking routines and QCG with CREST via a not yet released upstream patch, see github.com/grimme-lab/xtb/pull/1089/files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8eb1fae33223`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.