# Issue

**Title:** Build the TPSA and RDBE tables during class initialization

## Description

`TPSADescriptor` and `RDBERule` assign their static table before filling it, so a thread that constructs one while another is doing the first construction can read an empty or partial table. With 64 threads released together on first use, TPSA silently returned 0.0 in 5 of 150 fresh JVMs, and `RDBERule` threw a `NullPointerException` in 12 of 150.

This follows the approach used in #1311 for `AtomValenceTool`: build each table in a private static factory and assign it to a static final field during class initialization. The table entries are unchanged. This fixes table publication during concurrent first construction of independent instances. Most of the diff is indentation, and `git show -w` shows the real change.

No timing-dependent regression test is added. A shared test JVM may already have initialized these classes before the test runs.

I ran `mvn -pl descriptor/qsarmolecular,tool/formula test` on JDK 21: 1459 tests in `qsarmolecular` (54 skipped) and 273 in `formula`, with 0 failures. The same stress check on this branch gave 0 failures in 150 runs for each class.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c984706cee52`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.