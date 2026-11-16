# Issue

**Title:** Optimize uniform Simpson

## Description

This PR shaves off ~15-20% of the time spent in Simpson uniform integration, depending on the system and the computer. Impact will mostly be felt when used with ForwardDiff (see PR #1163). Would be also be GPU compatible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c10be67dc76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.