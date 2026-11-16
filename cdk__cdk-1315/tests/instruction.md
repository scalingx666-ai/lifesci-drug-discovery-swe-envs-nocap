# Issue

**Title:** QueryAtomContainer.create no longer changes the query it is given

## Description

`QueryAtomContainer.create(src, opts)` changed the query atoms of `src` when `src` was already a query, e.g. parsed from SMARTS. `strip()` returned the leaves it kept, and the `and()`, `or()` and `negate()` calls that combine them change the expression they are called on. After one call `[!#6]C` became `[!!#6]C`, so the caller's query matched carbon, and `[#7,#8]` grew on each call until the expression was cyclic and `Expr.toString()` overflowed the stack.

`strip()` now copies the leaves it keeps. Two tests in `QueryManipulationTest` cover it, and `testQueryNotChanged` fails without the change. The isomorphism and SMARTS tests pass.

Found while adding the `MCS` class in #1314.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52ac617802a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.