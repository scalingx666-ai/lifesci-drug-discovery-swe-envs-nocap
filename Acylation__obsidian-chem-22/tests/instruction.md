# Issue

**Title:** Modify default smiles-drawer options

## Description

- Change the default value of `scale` to 1, aiming to solve #14 
- Disable `compactDrawing` option by default,  & updates #20 
- Provide config UI prototype in the plugin setting tab

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37b01cc00e3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.