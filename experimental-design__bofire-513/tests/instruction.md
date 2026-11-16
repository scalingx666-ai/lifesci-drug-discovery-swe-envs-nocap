# Issue

**Title:** Mark `DesirabilityObjective` as only abstract

## Description

The `DesirabilityObjective` was by accident also marked as a real objective. This can lead to issues with pydantic for serialization and desiralization. cc: @LukasHebing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1c71f126143`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.