# Issue

**Title:** Support trajectory frames with differing atom counts

## Description

Uses the canonical variable-frame parser from aligfellow/xyzgraph#62. Adds the opt-in `--var-atoms` / `var_atoms=True` path, rebuilds each frame's graph independently, and derives orientation from a matching trajectory frame.

Depends on aligfellow/xyzgraph#62. The branch temporarily resolves xyzgraph from that PR's commit; switch back to the published `xyzgraph>=1.6.15` release before merge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b07ed98cc1bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.