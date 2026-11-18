# Issue

**Title:** Minor fixes

## Description

Suggested by AI bot nameearly in PR #462 (which also contained wrong changes).
- Add missing deallocation of quick_molspec%AtomDistance
- Do not zero qick_molspec%extchg for external points which do not carry external charges

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `750373e13573`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.