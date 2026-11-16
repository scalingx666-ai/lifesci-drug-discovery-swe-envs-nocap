# Issue

**Title:** Fixed TREXIO norm problems

## Description

QP produces correct TREXIO files now, checked with `trexio check-basis`.

- `qp_import_trexio` sets `ao_normalized` to `false` and multiplies the AO coefs by the normalization factor before storing them
- `qp_import_trexio` sets `primitives_normalized` to `true` and writes the normalization factors in the EZFIO. Those factors are used in QP. This avoids changing the AO coefficients of the primitives.

# Important

- I moved `ao_normalized` and `primitives_normalized` from `ao_basis/` to `basis/`. This will require a big recompilation of QP.
- `ao_normalized` was reversed: `true` meant `false` and `false` meant `true`. So the default is now `false` to enforce backward-compatibility.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `360aae7a104a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.