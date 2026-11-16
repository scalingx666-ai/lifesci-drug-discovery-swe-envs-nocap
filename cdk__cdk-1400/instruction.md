# Issue

**Title:** Keep Gaussian input writer outputs independent

## Description

Constructing a GaussianInputWriter replaces the static destination used by every instance, redirecting earlier writers' output. Closing one writer also closes that shared destination.

Make the buffered destination an instance field. Add a regression with valid 3D helium and neon fixtures that checks interleaved output separation and writing after the other writer closes.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), 696fd9797 against d12b2fc991:

- Module and dependency build passed.
- GaussianInputWriterTest: 12 passed, no failures, errors or skips.
- storage/io: 406 passed, no failures, errors or skips.
- With the production file from d12b2fc991 and the new test kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d12b2fc99198`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.