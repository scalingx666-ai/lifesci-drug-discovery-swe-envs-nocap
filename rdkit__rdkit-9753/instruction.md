# Issue

**Title:** Fix ring type after legacy SSSR symmetrization

## Description

#### Reference Issue

Regression in legacy ring finding algo introduced in #9105

#### What does this implement/fix? Explain your changes.

Legacy ring finding left symmetrized rings marked as plain SSSR. This caused the SMILES writer to recalculate the rings and could change stereochemistry during a SMILES round trip.

@ricrogz do you mind having a look at this PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0f3e7343197`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.