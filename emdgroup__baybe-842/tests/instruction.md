# Issue

**Title:** Wire CandidatesProtocol into SubspaceDiscrete

## Description

and #796.

The PR finally integrates the new `CandidatesProtocol` interface into `SubspaceDiscrete`, replacing the `parameters`/`exp_rep` architecture. 

Calls using the legacy arguments are still supported using a deprecation mechanism. Because supporting positional-only calls requires some custom `__init__` logic, the PR also absorbs the previous deprecation logic into the same method, resulting in a single place where legacy arguments are handled, and allowing us to drop all legacy attribute definitions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9f7a9b968eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.