# Issue

**Title:** Count 8- and 9-membered rings in SmallRingDescriptor

## Description

`SmallRingDescriptor` documents rings of size 3 to 9 and reports `nRings8` and `nRings9`, but the enumeration stops at 7. Both counts are therefore always 0, and those rings are missing from `nSmallRings`. Cyclooctane returns `nRings8` = 0 instead of 1.

This extends the enumeration to 9 and updates the adjacent comment. The finder continues to exclude cycles with a chord.

This changes published values. A sweep comparing the original implementation with a patched copy using the same bound change found 85 changed result vectors among 5,675 molecules, confined to `nSmallRings`, `nRings8` and `nRings9`. All 24 existing validation molecules passed.

The aromaticity detection rules are unchanged. Outside that sweep, `nAromRings` can also increase when an added 8- or 9-membered ring consists entirely of bonds already marked aromatic through smaller rings.

The new test checks a 7-membered control, 8- and 9-membered rings and their `nSmallRings` totals, and exclusion of a 10-membered ring.

On Linux with JDK 21, `mvn -pl descriptor/qsarmolecular test` reported 1460 tests, 0 failures, 54 skipped. With the production file restored to the base and the new test retained, the test fails at the 8-membered ring with `expected: <1> but was: <0>`.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c984706cee52`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.