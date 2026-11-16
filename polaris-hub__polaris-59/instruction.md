# Issue

**Title:** Fix issues due to the string representation of the HubOwner

## Description

## Changelogs

- Add the `__str__()` method to `HubOwner` to fix an issue where the computed artifact ID wasn't correct.
- Properly slugify the artifact ids when uploading to Hub.

## Discussion
This was encountered by @zhu0619 and during a user test with @FNTwin. A bug otherwise occurs at: 
- https://github.com/polaris-hub/polaris/blob/main/polaris/hub/client.py#L528C25-L528C42
- https://github.com/polaris-hub/polaris/blob/main/polaris/evaluate/_results.py#L118

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2a2295dc2ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.