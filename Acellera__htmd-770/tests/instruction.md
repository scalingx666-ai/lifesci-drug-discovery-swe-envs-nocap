# Issue

**Title:** Update .lgtm.yml

## Description

Update the `.lgtm.yml` script to exclude javascript files from the result (now that there is no js in the project)

In response to https://discuss.lgtm.com/t/alerts-in-deleted-files/1138

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d48eb862161b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.