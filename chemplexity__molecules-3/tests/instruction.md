# Issue

**Title:** Fix failing CI: correct planar crossing threshold for ultra-large corpus row 21714

## Description

The `layout/engine/audit-corpus` test suite was failing because the assertion threshold for `visibleHeavyBondCrossingFailureCount` on corpus row 21714 (a large multi-arm peptide) was set to `≤ 4`, but the layout engine consistently produces `6` residual planar crossings for this molecule.

## Change

- Updated the crossing threshold in `tests/layout/engine/audit-corpus.test.js` from `<= 4` to `<= 6` to match the algorithm's actual output for this ultra-large molecule.

```diff
-      audit.visibleHeavyBondCrossingFailureCount <= 4,
-      `expected at most 4 planar crossings, got ${audit.visibleHeavyBondCrossingFailureCount}`
+      audit.visibleHeavyBondCrossingFailureCount <= 6,
+      `expected at most 6 planar crossings, got ${audit.visibleHeavyBondCrossingFailureCount}`
```

The cleanup pipeline does successfully reduce crossings from the high initial count, but the previous ceiling of 4 was more aggressive than the current algorithm achieves for this specific molecule. The test remains a meaningful quality gate at the corrected bound.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1ef8d4edd7f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.