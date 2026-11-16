# Issue

**Title:** Least Squares Tensor Hypercontraction (LS-THC) for ERIs (Part 1)

## Description

## Description
In this PR, we implement a pilot version of least squares tensor hypercontraction (LS-THC)... factoring 4-index ERIs (O(N^4)) into two-index quantities (i.e. $(mn|rs) = x_{m}^{P}x_{n}^{P}Z^{PQ}x_{r}^{Q}x_{s}^{Q}$). In the LS-THC formulation, $P$ and $Q$ are derived from grid points, and

$x_{m}^{P} = w_{P}^{\frac{1}{4}} \phi_{m}(x_{P}, y_{P}, z_{P})$,
$E^{PQ} = x_{m}^{P}x_{n}^{P}(mn|rs)x_{r}^{Q}x_{s}^{Q}$
$S^{PP'} = (x_{m}^{P}x_{m}^{P'})^{2}$
$Z^{PQ} = (S^{PP'})^{-1} E^{P'Q'} (S^{QQ'})^{-1}$

This is based off of the work of [Parrish et al. (2012)](https://pubs.aip.org/aip/jcp/article/137/22/224106/194901/Tensor-hypercontraction-II-Least-squares)

These quantities can be constructed integral-direct and non-iteratively. No four or even three-index quantities are stored, thereby allowing for the future development of efficient, low-memory quantum chemistry algorithms in Psi.

This is a PR in a series of planned PRs that will involve:
1.) LS-THC-JK (integral-direct SCF without recomputing ERIs every iteration and faster K construction)
2.) LS-THC-MP2
3.) Local grid implementation of LS-THC to allow for use in local correlation methods (DLPNO-MP2, DLPNO-CCSD/(T))

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Added Python interface (Pybind) for building LS-THC quantities that allow for rapid prototyping of new methods involving THC
- [x] Developed infrastructure for the development of alternate ways to perform THC (i.e. PF-THC)

## Dev notes & details
- [x] Implemented LS-THC C/Py-side for future QC methods

## Questions
- [x] Is this the proper way to export this object Py-side?

## Checklist
- [x] Tests added for any new features
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ee8acbb6904`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.