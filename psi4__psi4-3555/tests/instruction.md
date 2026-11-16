# Issue

**Title:** Fix order-dependent mixed-basis ECP integrals

## Description

## Description

I ran into this while debugging an ECP-F12 problem in my own calculations, which I reported separately in #3554. While tracing that issue, I found that the mixed-basis ECP integrals themselves were order-dependent, even without running an F12 calculation.

For a single iodide ion with def2-SVP and def2-TZVP, both basis sets contain the same iodine ECP definition. Swapping the two bases should therefore just transpose the integral matrix, but the results disagree. In the tested build, the maximum difference is about 3.662 before this change and 8e-15 after it.

The ECP engine is currently initialized using only the bra basis's maximum angular momentum. In this example, that is 2, while the ket needs 3. This patch uses the larger value from the two bases.

Related to #3554. This fixes the mixed-basis integral problem; ECP-F12 support remains a separate question.

## User API & Changelog headlines

- Correct mixed-basis ECP integrals when the ket basis has a higher maximum angular momentum than the bra.

## Dev notes & details

- Change the orbital angular-momentum bound passed to LibECPInt. The ECP operator still comes from the bra basis, and the derivative order is unchanged.
- Add eight regression cases: SVP/SVP, SVP/TZVP, SVP/QZVP and TZVP/QZVP, each with Cartesian and spherical functions. The iodine ECP definitions are identical in these basis files.
- Built and tested `f234e73` (Psi4 `1.12a1.dev33`) before and after the patch. Before: six mixed-basis cases fail and the two equal-basis controls pass. After: all eight new cases pass, along with the existing ECP ghost, SCF ECP and basis ECP checks, for 11 passing tests in total.
- The branch is based on `1fb8968`. Both affected files are unchanged from the tested base above; this newer base has not been rebuilt locally.

```sh
# From the directory containing the source and build directories:
PYTHONPATH="$PWD/psi4-build-clean/stage/lib" OMP_NUM_THREADS=1 python -m pytest \
  psi4/tests/pytests/test_ecp.py \
  psi4/tests/scf-ecp/test_input.py \
  psi4/tests/basis-ecp/test_input.py -q
```

## Questions

None at the moment.

## AI

Codex was used to assist with debugging, testing.

## Checklist

- [x] Regression tests added.
- [x] Relevant existing ECP tests run locally.
- No documentation change is needed for this correction to the existing integral API.

## Status

- [x] Ready for review.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fb8968fe95e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.