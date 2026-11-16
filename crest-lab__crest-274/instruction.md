# Issue

**Title:** Restore multilevel turn-off function

## Description

`-nomlo` or `--no-multilevel` via the command line
or
`multilevelopt = false` in the toml input file

Also, one addition to the CMake build

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5cd626f65fed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.