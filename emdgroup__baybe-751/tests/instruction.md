# Issue

**Title:** Fix Shap for Numpy 2.4+

## Description

Since numpy2.4+ it's not possible anymore to assign an array of shape (1,) to a scalar

This has broken some of the py313 tests because they are forced to install newer versions of numpy

The fix involves unsqueezing the output of our model wrappers that go into the shap workflow form `(N,1)` to `(N,)`

There is a related issue that cannot be fixed in baybe which is a bugged line in the Maple module of shap, for this PR these tests are xfailed for numpy>=2.4

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a87f3645a522`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.