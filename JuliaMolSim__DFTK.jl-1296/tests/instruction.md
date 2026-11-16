# Issue

**Title:** fix save_scfres fallback signature

## Description

calling `save_scfres(:json, ...)` with a plain symbol `:json` would hit the fallback and produce a misleading error "json extension not available". With `::Val`, it correctly raises a `MethodError` instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efca39278617`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.