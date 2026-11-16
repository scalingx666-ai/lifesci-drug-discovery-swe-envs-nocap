# Issue

**Title:** fix(workflow): scanner resolves generic 'analysis' node so teaching templates run

## Description

Completes the analysis-node wiring (#413). The scanner only ran `_resolve_software` for UNIFIED_CALC_NODES, so a generic `analysis` node (with `params.type`) was never resolved to its specific handler — it stayed `analysis`, missed ANALYSIS_NODES routing, hit the submitter, and failed with 'No engine registered for analysis'. Now resolves `analysis` too.

**Verified end-to-end** on an isolated local backend: the MLP MD pipeline template (structure_input → MLP MD → md_analysis → export_data) runs **4/4 complete, 0 failed** with MACE on CPU — no HPC.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `069fb7ff72d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.