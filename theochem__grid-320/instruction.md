# Issue

**Title:** Feature/robust poisson split2

## Description

This PR implements **Split 2** of the Double-Split-Plus-Solve architecture, completing the robust Poisson solver pipeline.

This PR depends on #319 (Split 1) and currently includes its commits as this branch was branched off PR (split1).

While Split 1 (#319) successfully subtracts the extremely sharp promolecular atomic cores, the remaining residual density can still contain sharp multi center features (bonding density/polarization) or negative lobes. This PR implements a second split to analytically fit and extract this remaining density.

By utilizing `scipy.optimize.nnls` with a geometric progression of Gaussian basis exponents, we perform a nnls fit to capture the multi center bonding density. Because Gaussians have exact analytical potentials, this leaves only a tiny, perfectly smooth numerical residual for the BVP solver to integrate, meaning it converges without any risk of crashing or instability.

once pr(split1) #319 gets updated (if required ) after review  and gets merged to master, ill rebase this PR then the git diff (amount of new lines added or deleted ) will reduce accordingly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49985fd4d44a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.