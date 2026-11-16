# Issue

**Title:** Small docstring fix for `sumo-dosplot`

## Description

Just noticed that the docstring for `zero-energy` in `sumo-dosplot` was incorrect (duplication of `zero-line` which has different behaviour), so just a small update

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fff98bcecece`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.