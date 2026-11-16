# Issue

**Title:** Fix 0D stereo parity when reading and writing molfiles

## Description

A 0D molfile gives tetrahedral stereo as atom parity (V2000) or CFG (V3000), defined over the neighbours in atom-number order with an implicit hydrogen counted as the highest. The reader applied it in bond-block order, so swapping two bond lines in an L-alanine molfile gives D-alanine. The V3000 writer ranked the implicit hydrogen equal to the last atom, so `N[C@@H](C)O` was written with the inverted CFG. The two errors cancel on some molecules, so they are fixed together.

The reader now sorts the neighbours by atom number, and the writer ranks the implicit hydrogen above every atom. `writeParityImplH` and `writeParityImplHInverted` expected the CFG values from the old tie and are corrected.

The test commit fails without the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e7373ea174f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.