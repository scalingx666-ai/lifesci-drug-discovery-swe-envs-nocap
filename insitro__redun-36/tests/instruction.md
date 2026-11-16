# Issue

**Title:** Add missing data.tsv and fix cleanup default

## Description

Addresses #35 

## Description

- Add two missing files to the docker example: `data.tsv` and `.redun/redun.ini`.
- Changes back the default value for the `cleanup` argument for docker containers.

## Testing

- Reran the docker example to confirm the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c7452689b55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.