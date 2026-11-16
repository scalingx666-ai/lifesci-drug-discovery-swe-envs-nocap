# Issue

**Title:** Proposal for badly failing cases

## Description

I know these failures should not happen (as the error message says :smile:), but they do ... and unfortunately often in longer-running workflows where it's not super easy to figure out why and further it's super annoying that the entire computation crashes because of this.

Here is one proposal to deal with it ... namely just fall back to an expensive, but hopefully accurate orthogonalisation method. One could also implement throwing some special exception, which can then be handled higher up (e.g. by perhaps aborting the LOBPCG at the current state and flagging non-convergence). Not sure, what is better.

CC @antoine-levitt

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8b3f0fcce28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.