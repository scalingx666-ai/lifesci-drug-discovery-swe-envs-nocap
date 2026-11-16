# Issue

**Title:** Update ROCS scorers and fix the shape matching tutorial

## Description

. Updates the ROCS scorers to the version used in production and fixes the shape matching tutorial so it runs from start to finish.

## Changes

- Scorers can choose what the alignment optimizes (`shape`, `combo` or `color`): `score_type` for RDKit, `opt_mode` for CDPKit and `optimization_mode` for OpenEye
- RDKit scores no longer depend on the input pose (rdkit/rdkit#8513)
- Tversky score variants, per-molecule timeouts, and OpenEye color types for the RDKit and CDPKit scorers
- Fix `SequenceRNN` crash on CPU-only machines
- Fix the tutorial paths and cell order, and rerun the notebook
- Collect the scorer tests into one `tests.py` (117 tests, all picked up by `unittest discover`)

Note: the conformer generators now protonate and canonicalize tautomers by default, and the CDPKit timeout drops from 3600 s to 20 s, so existing scores can change. Details are in the change log.

@martin-sicho

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0763022238a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.