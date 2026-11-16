# Issue

**Title:** Update QCG for aISS use (xTB-IFF becomes outdated)

## Description

To use the automated Interaction Site Screening (aISS) instead of the xTB-IFF stand-alone, the xtb version 6.5.0 or newer is required. If the xTB-IFF should still be used, the "-xtbiff' flag has to be provided.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19a8f00f3b9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.