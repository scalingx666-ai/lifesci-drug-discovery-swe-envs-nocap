# Issue

**Title:** feat: remove molecule comparison feature

## Description

Remove the side-by-side comparison overlay, tray, and context. The feature had significant UX issues (transparent overlay, unclear close/back flow, structure images not loading) and limited utility.

Deleted: ComparisonContext, ComparisonTray, ComparisonView, AddToCompareButton, and their tests.
Cleaned references from App.tsx, MoleculeCard, and 6 chem tool views.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cdf923a0ebf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.