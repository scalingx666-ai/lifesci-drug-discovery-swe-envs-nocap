# Issue

**Title:** Honor the configured maximum in RDBERule

## Description

RDBERule.validate() ignores the maximum supplied to setParameters() and always uses 30. Compare against max instead.

Add regression tests for rejection above a maximum of 10, acceptance at exactly 10, and acceptance of RDBE 36 with a maximum of 40.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), 45f164282 against d1ed11eeb:

- Module and dependency build passed.
- RDBERuleTest: 21 passed, no failures, errors or skips.
- tool/formula: 280 passed, no failures, errors or skips.
- With the production file from d1ed11eeb and the new tests kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1ed11eeb341`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.