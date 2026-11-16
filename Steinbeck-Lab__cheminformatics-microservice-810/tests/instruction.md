# Issue

**Title:** test(toolkits): close coverage gap on format-detection code paths

## Description

Codecov flagged this PR's diff coverage below target (92.92% vs 93.67%), driven by helpers.py sitting at 84% for the new auto-detect module. Adds tests for the native-Mol fallback's error paths, resolve_input_smiles, unsupported-format rejection, the molblock SDF-delimiter trim, and split_xyz_frames'/_is_plausible_atom_row's edge cases -- 84% -> 99% on this file, 3 lines remaining (one unreachable given get_smiles_opsin's current error handling, two narrow CDK-fallback branches not worth constructing brittle tests for). Also fixes standardize=True on the new xyz/molblock/inchi native path to reparse with removeHs=False, consistent with the rest of the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b164d2301a3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.