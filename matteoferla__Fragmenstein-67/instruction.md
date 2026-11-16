# Issue

**Title:** fix: add missing frontend constants, fix start.sh for macOS

## Description

## Summary
- **Missing file**: `src/lib/constants.ts` was never committed because the root `.gitignore` matches `lib/`. Added the file and an exclusion for `web/frontend/src/lib/`.
- **start.sh**: uses `python3` with `python` fallback — macOS only ships `python3`.
- **Outcome colours**: match `LabBench.category_labels` (acceptable, deviant, equally sized, unstable, timeout, too distant, crashed).

## Test plan
- [x] `cd web && ./start.sh` works on macOS (python3) and Linux (python/python3)
- [x] http://localhost:3000 loads without module-not-found errors

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fa33f4aea26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.