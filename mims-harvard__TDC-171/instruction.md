# Issue

**Title:** fix two bugs in zaleplon_mpo: 1. addH (add hydrogen atom when evaluat…

## Description

…ing isomer function); 2. smiles2formula; considering the old users, previous version is kept, the name is zaleplon_mpo_prev

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68308e3dfdd1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.