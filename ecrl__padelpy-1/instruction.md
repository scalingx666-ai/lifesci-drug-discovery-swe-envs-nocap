# Issue

**Title:** Function timeouts, process attempts

## Description

- "from_smiles" and "from_mdl" now accept an optional timeout argument
- "from_smiles" and "from_mdl" will now attempt conversion three times before throwing an exception
    - this _should_ reduce indeterminate failures caused by PaDEL-Descriptor
- exceptions thrown by PaDEL-Descriptor are now decoded to UTF-8

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95af69334654`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.