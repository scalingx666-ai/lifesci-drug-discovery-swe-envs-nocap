# Issue

**Title:** Hessian Rot/Trans Projection after Mass-weighting

## Description

Before the projection of the rot/trans modes were done before the mass weighting. In the dxtb project as well as the gaussian white paper reads as if the correct way to do this is, however, after the massweighting. this lead to problems as no projection was done for linear molecules resulting in wrong frequencies. This patch should elevate this problem, works also for fixed atoms. Testing on the in #693  mentioned linear water molecules yields now two -1802.38 cm^-1 modes. the ordering in the vibspectrum file also seems to be correct now.

This should therefore close #693 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68fe777a0241`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.