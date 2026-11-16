# Issue

**Title:** Expr.or now returns TRUE when either side is TRUE

## Description

`Expr.or()` treated a TRUE operand like FALSE and dropped it, so `x.or(TRUE)` gave `x` and `TRUE.or(FALSE)` gave FALSE. The SMARTS `[*,N]` was read as `N` and matched none of the carbons in CC=CC, and `C~,=C` matched one bond instead of three.

`or()` now returns TRUE when either side is TRUE; FALSE and NONE are still dropped. `MDLV2000Reader` built its atom lists by OR-ing onto TRUE, so it now starts from FALSE. It was the only place in CDK that did this, but code outside CDK that ORs onto the default expression of a new `QueryAtom` or `QueryBond` (TRUE) should also start from FALSE.

`ExprTest.alwaysTrueOr` and `SmartsPatternTest.orWithAnyAtomOrBond` fail without the change. The isomorphism, SMARTS and MDL reader tests pass.

Found while working on the MCS class in #1314.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `861f99562523`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.