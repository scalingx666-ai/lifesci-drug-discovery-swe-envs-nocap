# Issue

**Title:** Skip elements outside the MMElementRule table

## Description

At base `4253aa225f`, `MMElementRule.validate` throws a `NullPointerException` for formulas such as iodobenzene (C6H5I): it unboxes the table's maximum count for every element, and iodine has no entry. The class Javadoc says elements that are not in the table are skipped.

Check for a missing limit before comparing counts, so unlisted elements are skipped as documented. The tables are unchanged. Tests cover C6H5I and the sodium adduct [C6H12O6Na]+, which validate to `1.0`; the existing C2H200 test still returns `0.0` for an excessive listed-element count.

Checked on Linux (JDK 21, Maven): with production code at `4253aa225f`, the new tests fail (both throw `NullPointerException` before their assertions: iodine and sodium have no table entry, and every listed count is within its limit). With the fix, `MMElementRuleTest` passes all 9 tests and `tool/formula` all 275.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6903673ce8da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.