# Issue

**Title:** Skip blank lines at XYZ frame boundaries

## Description

XYZReader can throw NoSuchElementException when otherwise valid input ends with blank lines, preventing the parsed frames from being returned.

Read frame headers until readLine() returns null and skip blank lines where the next atom count is expected. Preserve empty title lines and existing atom-row parsing. Temporary unreadiness no longer ends parsing; streaming input is read through EOF.

Add one- and two-frame regressions through StringReader and InputStream, checking frame and per-frame atom counts, plus leading, intervening and trailing boundary whitespace, an empty title and malformed-coordinate coverage.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), 65a931f6a against 5118b85c0:

- Module and dependency build passed.
- XYZReaderTest: 20 passed, no failures, errors or skips.
- storage/io: 413 passed, no failures, errors or skips.
- With the production file from 5118b85c0 and the new tests kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `375eecd4bad3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.