# Issue

**Title:** Include bromine in RDBE calculations

## Description

At base `6903673ce8`, `RDBERule.validate` throws a `NullPointerException` for bromobenzene (C6H5Br) because the valence table has no bromine entry. Its DBE is 4: one ring and three double bonds.

Add bromine with valence 1, matching fluorine, chlorine and iodine. Tests check that validation returns `1.0` and the first RDBE value is `4.0` for bromobenzene and a chlorobenzene control. Other elements missing from the table are outside this change.

Checked on Linux (JDK 21, Maven): with production code at `6903673ce8`, the bromobenzene test fails (from the code, `validate` dereferences the missing valence entry) while the chlorobenzene control passes. With the fix, `RDBERuleTest` passes all 18 tests and `tool/formula` all 275.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6903673ce8da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.