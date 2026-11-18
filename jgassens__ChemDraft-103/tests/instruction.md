# Issue

**Title:** Preserve gradient shading when recoloring

## Description

Recolor gradient stops relative to the base color so highlights and shadows remain intact. Add coverage for changing a radial sphere from blue to red.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `303874fcb127`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.