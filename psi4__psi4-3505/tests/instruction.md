# Issue

**Title:** Fix MP2-F12 when linear dependencies are removed from a basis

## Description

.

Three related problems kept MP2-F12 from running once linear dependencies were removed:

* `orthogonal_complement` built the MO overlap as S12 C2, labelling its rows with the *orbital* count of space1 while actually producing one row per *basis function*. Those agree only when nothing was removed from space1; otherwise the gemm aborts with a row/column mismatch. Transform both sides, C1^T S12 C2.

* `orthogonalize` zeroed the dependent directions of S^-1/2 instead of dropping them, so the RI space kept the full basis dimension and handed its null vectors on to CABS. Switch to canonical orthogonalization, X = U_kept s_kept^-1/2, when there is something to remove; bases without linear dependencies still get the symmetric orthogonalization as before.

* MP2F12 set `nobs_` from the number of basis functions rather than the number of orbitals, which overruns the reference coefficient matrix and mis-sizes the one-electron MO integrals.

The orbital space tests now cover linear dependencies in the orbital basis, in the RI basis, and in both.

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] MP2-F12 no longer aborts with "Matrix::gemm error: Number of rows and columns do not match" when linear dependencies are removed from the orbital basis (#3498).
- [x] The RI space now really drops linearly dependent vectors instead of retaining them as null vectors, so CABS comes out orthonormal and with the right dimension.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] OrbitalSpace::orthogonal_complement built the MO overlap as S12 C2 but allocated it with space1.C()->colspi() rows. That product has one row per basis function of space1, not one per orbital, and the two only agree when nothing was removed from space1. It now transforms both sides, C1^T S12 C2. This is the immediate cause of the traceback in the issue.
- [x] orthogonalize, which builds the RI space, zeroed the dependent directions of S^-1/2 instead of dropping them. That leaves a rank deficient square matrix, so the space keeps claiming the full basis dimension and hands its null vectors on to CABS, which is then not orthonormal. It now uses canonical orthogonalization, X = U_kept s_kept^-1/2, when there is something to remove. Bases with no linear dependencies still get symmetric orthogonalization as before, so nothing changes for cases that already worked.
- [x] MP2F12::common_init took nobs_ from basisset()->nbf() rather than the number of orbitals. Once linear dependencies are removed that overruns the reference coefficient matrix in convert_C and mis-sizes the one-electron MO integrals in form_oeints, which does C1^T h C2 and so returns nmo by nmo.
- [x] tests/pytests/test_orbitalspace.py now runs the existing orthonormality checks over four cases: no linear dependencies, dependencies in the orbital basis, in the RI basis, and in both. The orbital basis cases truncate the SCF coefficients rather than leaning on an ill conditioned basis, so they are deterministic. A CABS dimension check is also added.

Testing done locally (macOS arm64, conda toolchain, Einsums 1.1.5):
- Water / d-aug-cc-pVTZ with S_TOLERANCE 1e-4 removes 2 of 126 orbitals and reproduces the reported gemm error on master. With this branch it runs: -76.3880318670 with nothing removed, -76.3879290140 with 2 removed, -76.3874095731 with 6 removed (S_TOLERANCE 1e-3). The issue's own example (HCN dimer, d-aug-cc-pVQZ) is too large to run here, so this is the same code path on a smaller system.
- On master the new test cases fail as expected: the orbital basis ones error in the fixture on the gemm, and ribs_lindep fails the CABS orthonormality check without any crash.
- ctest mp2f12-1 and dfmp2f12-1 pass with unchanged energies, and the quicktests label is 190/190.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] Used to create local test cases in order to reproduce the issue.

## Checklist
- [x] Tests added for any new features
- [ ] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e5d928bd398`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.