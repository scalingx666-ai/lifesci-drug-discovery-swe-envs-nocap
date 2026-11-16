# Issue

**Title:** New Quadrature Grids

## Description

This is the new pull request replacing #103.

- The original commits are still preserved.
- The grid classes and their tests are now consistent with the new API.
- Only SingleTanh passes the integration tests and this is after playing around with the tests

For reference the following quadrature are here: ExpSinH,  LogExpSinh, ExpExp, SingleTanh, SingleExp, SingleArcSinhExp.

References
--------------
- [Boost](https://www.boost.org/doc/libs/1_68_0/libs/math/doc/html/math_toolkit/double_exponential.html) has implementation of sinh-sinh, exp-sinh added. 
- The following paper "Improving the Double Exponential Quadrature
Tanh-Sinh, Sinh-Sinh and Exp-Sinh Formulas" by
Dr. Robert A. van Engelen, Genivia Labs may be useful. They have a section on "Combining Tanh-Sinh with Exp-Sinh and Sinh-Sinh quadrature" and the section "A new method to improve Exp-Sinh quadrature convergence" with code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bfaa2761b83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.