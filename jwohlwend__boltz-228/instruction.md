# Issue

**Title:** Fix Boltz writing waters in mmcif format, issue #227.

## Description

Fix Boltz writing waters in mmcif format.  Fixes jwohlwend/boltz#227.  The ihm and modelcif modules used to write mmcif requires WaterAsymUnit instead of AsymUnit when writing waters.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfebd333e717`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.