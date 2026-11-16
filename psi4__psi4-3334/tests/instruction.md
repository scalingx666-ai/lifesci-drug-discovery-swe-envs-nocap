# Issue

**Title:** Optimize wK block in DirectJK: use clone() instead of N separate crea…

## Description

## Description

Optimize wK block in `DirectJK::compute_JK()` to use the same efficient pattern as J/K block.

**Author:** Konstantin Komarov (constlike@gmail.com), Department of Chemistry, Ulsan National Institute of Science and Technology (UNIST), Ulsan, South Korea (Prof. Seung Kyu Min group)

## User API & Changelog headlines

- [x] Performance improvement for range-separated functionals (wB97, wB97X, CAM-B3LYP, etc.)

## Dev notes & details

- [x] wK block now creates one `TwoBodyAOInt` object and clones it to N threads
- [x] Before: N calls to `factory->erf_eri()` + N calls to `update_density()`
- [x] After: 1 call + (N-1) `clone()` operations
- [x] `Libint2ErfERI` already supports `clone()`, same pattern as J/K block

## Questions

(none)

## Checklist

- [x] Tests added for any new features
- [x] All or relevant fraction of full tests run
  - `dft1`: wB97/wB97X (RKS, UKS) — all PASSED
  - `dft3`: wB97 with PK, OUT_OF_CORE, DIRECT, DF — all PASSED

## Status

- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73d3f5b48cf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.