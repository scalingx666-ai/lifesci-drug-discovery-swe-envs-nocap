# Issue

**Title:** Make n_components optional in multi-MP

## Description

I've always been a bit annoyed having to specify `n_components` in `MulticomponentMessagePassing` when it is only needed if `shared=True`. This PR makes it optional. I don't imagine there would be any backwards compatibility issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd535dd44252`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.