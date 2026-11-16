# Issue

**Title:** 168 refactor moltofingerprint pipeline element

## Description

- [x] Dissolve ABCMorganFingerprintPipelineElement
- [x] Add `bit2atom_mapping` to MolToRDKitGenFPElement for consistency
- [x] Test explainability with `MolToRDKitGenFPElement `

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d801fe7a8fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.