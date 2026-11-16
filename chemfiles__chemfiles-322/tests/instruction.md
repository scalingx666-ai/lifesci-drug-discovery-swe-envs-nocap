# Issue

**Title:** Expose {Frame,Topology}::clear_bonds to the C API

## Description

They are part of the public C++ API, so I think they should be part of the public C API too. No idea why they were left out initially.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49442411ab9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.