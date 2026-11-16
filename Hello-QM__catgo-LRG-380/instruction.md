# Issue

**Title:** fix(dos): parse adjacent signed PROCAR floats

## Description

## Summary
- Fix PROCAR parsing when VASP prints adjacent signed float values without whitespace, e.g. `0.00000000-0.40000000`.
- Parse projection values with a float regex instead of relying only on whitespace splitting.
- Add a regression test for adjacent signed float parsing.

## Why
Some PROCAR files contain values like `0.00000000-0.00000000` or `0.00000000-0.40000000`. The previous parser treated those as one token and failed with `could not convert string to float`.

## Verification
- `git diff --check` passed.
- `py -m py_compile extensions\dos-analysis\catgo_dos\io.py` passed.
- Manual parser assertion passed for `0.00000000-0.40000000 1.25E-03-2.50E+01`.
- Full pytest was not run because pytest is not installed in the current local Python environment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a697fe29c84c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.