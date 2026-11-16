# Issue

**Title:** Preserve atom mapping indices in CML round trips

## Description

CML round trips restore atom mapping indices as Strings, so calling `IAtom.getMapIdx()` throws `ClassCastException`.

Restore the reserved `cdk:AtomAtomMapping` scalar property as an Integer in the reader. Ignore malformed or overflowing mapping values with a warning, leaving them unset, and keep other custom atom properties as Strings.

Add round-trip tests for mapped ethane, an unmapped atom, and a numeric-looking String property, plus a reader test for malformed and overflowing mapping values.

Checked on Linux (Ubuntu 24.04.5 LTS, javac 21.0.12.1, Maven), ad2a81593 against d1ed11eeb:

- Module and dependency build passed.
- CMLRoundTripTest: 35 passed, no failures, errors or skips.
- storage/io: 407 passed, no failures, errors or skips.
- storage/libiocml: 107 tests run, 10 pre-existing skips, no failures or errors.
- With the production file from d1ed11eeb and the new tests kept, the test run fails.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6eea2f3a075c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.