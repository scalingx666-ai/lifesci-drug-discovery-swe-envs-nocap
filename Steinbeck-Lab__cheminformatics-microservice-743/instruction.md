# Issue

**Title:** feat: remove SMILES inline preview feature

## Description

Remove the debounced 2D structure preview below SMILES inputs. Redundant with the depiction tools and adds complexity (API dependency, debounce hook, loading/error states) for minimal user value.

Deleted: SMILESPreview, useDebounce hook, and their tests. Cleaned import and usage from SMILESInput.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d05813592248`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.