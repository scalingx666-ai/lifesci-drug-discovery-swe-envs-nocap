# Issue

**Title:** feat(viewer): raise bond-deferral threshold 8000 → 30000 atoms

## Description

The 8000-atom deferral (#507) made routine 20k-atom systems (zeolite + Pt-cluster trajectory, O13568 Si6144 Pt256) demand a 'Compute bonds' click on every open. The one-time on-load pair build at that size is sub-second and detection already runs async in the worker, so defer only truly massive structures. 11k kerogen / 20k zeolite now compute on load; tests updated to encode the new policy (5/5 green).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `003862acf721`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.