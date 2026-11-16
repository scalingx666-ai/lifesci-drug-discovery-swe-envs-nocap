# Issue

**Title:** Added confidence dumping

## Description

Added dumping of confidence metrics. We include the option to dump:

1. The full PAE confidence matrix (.npz)
2. The full PDE confidence matrix (.npz)
3. The per-token PLDDT (.npz)
4. A summary of the aggregated confidence (.json) including: PLDDT, iPLDDT, PDE, iPDE, iPTM, PTM, per-chain PTM, pair-chain iPTM and an aggregated confidence score computed as: (4 * PLDDT + iPTM) / 5

Use write_confidence_summary, write_full_pae and write_full_pde to turn off/on the confidence dumping. By default the PAE, PLDDT and the summary of the aggregated metrics get dumped.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb8e7dd6926d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.