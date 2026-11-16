# Issue

**Title:** Update DielectricAdjoint internal docs comments

## Description

I adjusted the comments, removing the inverse which corresponds to the linear solver call on an outer level.

A remaining minor inconsistency that I tripped over for a moment: in the math format we use $\varepsilon^\dagger$ which implies that $\varepsilon$ is the name for the dielectric function. However in code we use `ε::DielectricAdjoint` such that `mul_approximate(ε, δρ)` $\approx \varepsilon^\dagger \delta\rho$. What about writing `ε_adj` instead in code? Con: It's longer than 1 character, Pro: it avoids confusion.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5f5240e20de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.