# Issue

**Title:** libqt: put the Fortran BLAS/LAPACK prototypes in an anonymous namespace

## Description

## Description

`blas_intfc.cc`, `blas_intfc23.cc` and `lapack_intfc.cc` declare the Fortran BLAS/LAPACK entry points in `extern "C"` blocks at file scope. Following the review remark in #3551, the blocks are wrapped in an anonymous namespace: the prototypes are visible to their own translation unit only, the C-linkage symbols they name are unchanged.

## User API & Changelog headlines

- [x] None.

## Dev notes & details

- [x] `namespace { extern "C" { ... } }` around the existing blocks (`blas_intfc.cc:60-82`, `blas_intfc23.cc:44-67`, `lapack_intfc.cc:43-284`). Nine added lines, nothing removed.
- [x] The wrappers call the prototypes both as `F_XXX` and `::F_XXX`; both resolve, so the call sites are untouched. Checked with GCC 15 and Apple clang.
- [x] `lapack_intfc.h` has its own copy of the LAPACK block, but nothing includes it; left as is.

## Questions

- [x] None.

## AI

- [x] AI assistance: code, checking the lookup on both compilers, description.

## Checklist

- [x] No test: declarations only, no behaviour change.
- [x] No documentation change needed.

## Status

- [x] Ready for review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ced4201fa97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.