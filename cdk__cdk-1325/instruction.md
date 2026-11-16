# Issue

**Title:** Fix count fingerprint similarity and sparse intersections

## Description

Two fingerprint operations lose or misread features:

- `Tanimoto.calculate()` on count fingerprints for ethylamine (`CCN`) and ethanol (`CCO`) throws `ArrayIndexOutOfBoundsException`, while reversing the arguments returns `1/3`. Other trailing-bin counts silently give incorrect scores. The remaining second-fingerprint bins now use their own index.
- `IntArrayFingerprint.and()` repeatedly writes the first output slot. For example, intersecting `[1,2,3]` with `[1,2,3,4]` gives `[0,0,3]`. Advance the output index so every shared bit is retained.

Each fix is a separate commit. Regression tests cover both molecule comparison orders, unequal trailing counts, one empty count fingerprint, and repeated sparse intersections with negative, zero and positive hashes. Before the fixes, the focused tests had two failures and one error; all pass afterwards.

Validation: `mvn -o -q -pl base/isomorphism,tool/smarts,descriptor/fingerprint -am test` passes, including 226 isomorphism, 828 SMARTS and 229 fingerprint tests plus their dependency suites. Compiled with the project's `--release 8` configuration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e9aad649b83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.