# Issue

**Title:** fit_net_charge() used to mutate partial charges to LJ; elsewhere any …

## Description

…partial charge changes are temporary; V-S plotting made to be per atom, fixed to correctly plot changes to partial charges; xyz writer now removes charges properly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5a26c037607`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.