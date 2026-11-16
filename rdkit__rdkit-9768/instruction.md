# Issue

**Title:** Check ETKDG total improper energy after summing it in _checkKTerms

## Description

_checkKTerms compared totalEnergy against nCenters * planarityTolerance before the loop that accumulates it, so the total planarity check in the all-in-one ETKDG path always saw 0.0 and never fired. Only the per-term limits were applied, which allow far larger out-of-plane distortions than the legacy implementation accepts. Test the total once all contributions have been summed.

Found and implemented fix with the help of Claude Opus 5.5

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73268ba001e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.