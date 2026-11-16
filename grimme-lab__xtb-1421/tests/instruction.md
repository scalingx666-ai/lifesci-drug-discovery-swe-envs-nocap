# Issue

**Title:** Fix monoatomic hessian initialization

## Description

This was initially introduced in 

In hessian.F90, `isqm` is only initialized if `mol%n > 1`. But it is [unconditionally copied into freq](https://github.com/grimme-lab/xtb/compare/main...TyBalduf:xtb:fix/monoatomic-hessian-initialization?expand=1#diff-565fb80b708ce0e4f18fcaee3a834915ceb64970c6e0911b3c0f9b59829862d5R481). The un-initialized value depends on the compiler/heap-layout, but can essentially be any random value. `h` is actually initialized to zero elsewhere, but moving the initialization outside the `mol%n > 1` block feels clearer about the intent.
 
This has manifested as  where the entropy/free energy winds up being infinite in many cases. The first commit addresses this issue.

Incidentally, I also fixed that the reduced mass for the translational mode would be printed as Infinity, since `xsum==0.0` in this case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.