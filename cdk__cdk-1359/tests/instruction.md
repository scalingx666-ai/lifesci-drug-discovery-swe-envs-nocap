# Issue

**Title:** Exclude bonds to hydrogen from order-specific bond counts

## Description

`BondCountDescriptor` documents that it does not consider bonds to hydrogen, and its all-bonds branch skips them, but the order-specific branch counts them. Ethanol therefore gives eight single bonds once its hydrogens are explicit, instead of two.

This applies the same exclusion to the order-specific branch. In practice only `s` changes, since hydrogen has no multiple bonds, and molecules without explicit hydrogen atoms keep their values. The new test checks ethanol before and after `convertImplicitToExplicitHydrogens`, and the all-bonds count.

I ran `mvn -pl descriptor/qsarmolecular test` on JDK 21: 1458 tests, 0 failures, 54 skipped. Without the change the new test fails with `expected: <2> but was: <8>`.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c35315aa92e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.