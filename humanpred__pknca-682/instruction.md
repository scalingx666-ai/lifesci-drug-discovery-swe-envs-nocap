# Issue

**Title:** feat: validate the LLOQ values in PKNCAconc()

## Description

PKNCAconc() checked only that the lloq column or scalar was numeric, with a checkmate error.

- Every non-missing lloq value must now be finite, not NaN, and greater than zero. NA stays allowed, since missing LLOQs are ignored downstream.
- A column or scalar that is entirely NA of any class (for example the logical NA of a column read from a file with no LLOQ) is accepted and stored as numeric NA. An integer column stays integer; an all-NA integer column becomes double.
- A units column is accepted and stored as given; the checks use the plain numbers.
- Anything else (a non-numeric class with a value, zero, negative, Inf, NaN) is the classed error pknca_error_conc_invalid_lloq, whose message names up to five offending values, then "...", or the class.

Tests pin the exact class and message for each refused case and the accepted all-NA, mixed, units and valid cases. The lloq roxygen and NEWS.md describe the behavior.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e15c65e0d1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.