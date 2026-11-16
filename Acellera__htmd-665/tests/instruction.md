# Issue

**Title:** Silence pyemma version warnings

## Description

Really the other PR was overkill. Those warnings are only thrown on the first import. So we might as well just import it once with a wrapper in `htmd.ui` and be done with it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9962ce0b3b75`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.