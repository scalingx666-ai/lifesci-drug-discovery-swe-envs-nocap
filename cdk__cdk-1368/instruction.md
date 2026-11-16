# Issue

**Title:** Match the element in common isotope lookups

## Description

At base `6e51f7b458`, `Isotopes.get(IElement.F, 18)` returns O-18 because the common-isotope fast path matches only the mass number. The Javadoc promises the isotope of the requested element and mass number, or null if it is not found.

Require the atomic number to match before checking the mass number, keeping the ordered early exit and the fallback to the element's isotope list. Tests assert non-null results with the requested element and mass number for F-18 and Xe-131, preserve the C-13 common-isotope hit, and check the documented null result for C-99.

Calculated masses can change when affected specified isotopes, such as fluorine-18 in [18F]FDG, are resolved through this lookup. From the mass-calculation code, this can affect `MolWeight`, `MonoIsotopic`, and `MostAbundant`; `MolWeightIgnoreSpecified` uses element averages and is unaffected. The isotope data are unchanged. The new tests check isotope identity and absence.

Checked on Linux (JDK 21, Maven): with production code at `6e51f7b458`, the new F-18 and Xe-131 tests fail (`expected: <9> but was: <8>` and `expected: <54> but was: <53>`). With the fix, `IsotopesTest` passes all 35 tests, and so do `base/core` (228 tests), `base/test-core` (732 tests), `tool/formula` (273 tests) and `base/test-standard` (1009 tests).

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e51f7b45816`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.