# Issue

**Title:** Fix chirality bug in MAPFingerprint using full molecule instead of substructure

## Description

## Summary
- Fixes the chirality code path in `_find_env()` which was calling `MolToSmiles(mol, ...)` on the **full molecule** instead of `sub_molecule`
- This caused the chirality mode (MAPC) to produce the same SMILES for every atom regardless of local environment
- Now correctly uses `sub_molecule` with `rootedAtAtom`, matching the non-chirality path
- Added regression test verifying enantiomers (L-alanine vs D-alanine) produce different fingerprints

Partial fix for #519 (addresses the chirality bug; `variant` parameter and MinHash support can be added in a follow-up)

## Test plan
- [x] All 8 MAP fingerprint tests pass (including new regression test)
- [x] Verified L/D-alanine produce identical fingerprints without chirality, different with chirality
- [ ] CI passes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `839001468ba8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.