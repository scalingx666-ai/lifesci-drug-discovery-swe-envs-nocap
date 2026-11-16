# Issue

**Title:** added wrapper for molscore package to provide access to common benchmarks

## Description

such as molopt/PMO and MolExp https://arxiv.org/pdf/2206.12411 & https://pubs.acs.org/doi/10.1021/acs.jcim.5c02316

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d082b3657137`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.