# Issue

**Title:** Clarify mRRHO treatment in thermochemistry output

## Description

Adds an RRHO/mRRHO label and notices explaining the treatment behind `G(RRHO)`, with appropriate reference. Negative cutoffs retain their existing RRHO behavior and now print a warning.

All existing functionality, calculations, defaults, energy labels, and numerical output are preserved. This PR only adds information to the printed output.

Validation:
- Meson build and the existing thermochemistry test pass.
- Actual output checked at `sthr=0`, `50`, `100`, and `-10`; numerical results are unchanged.
- Full local suite: 41 passes, 1 expected failure, and 2 failures (`gfn0`, `peeq`), also reproduced on unmodified `main`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `646a604a5286`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.