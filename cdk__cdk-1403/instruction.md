# Issue

**Title:** Ignore disabled elements when choosing the formula generator

## Description

For C 0–10 in the 119.9–120.1 mass window, adding H and O with bounds 0–0 incorrectly selects RoundRobin. It removes those disabled isotopes and fails when it accesses a second weight instead of returning C10.

Choose the generator using the number and smallest exact mass of isotopes with positive maximum counts. Keep the existing full-enumeration fallback for at most two enabled isotopes; it also handles all-disabled ranges.

Tests compare C-only results before and after adding disabled H/O in a window containing C10, check two enabled elements and all-disabled ranges, and cover the minimum-mass heuristic and continued RoundRobin selection.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), e96253285 against 6eea2f3a0:

- Module and dependency build passed.
- MolecularFormulaGeneratorTest: 28 passed, no failures, errors or skips.
- tool/formula: 283 passed, no failures, errors or skips.
- With the production file from 6eea2f3a0 and the new tests kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6eea2f3a075c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.