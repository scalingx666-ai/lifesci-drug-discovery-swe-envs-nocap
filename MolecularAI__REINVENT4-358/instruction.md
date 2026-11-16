# Issue

**Title:** fix: fragment components score NaN instead of crashing on unparseable fragments

## Description

LinkInvent fragment components only caught `ValueError`, but `cap_fragment` can return `None` for unparseable fragments and RDKit calls on pathological fragments (e.g. multi-bonded `*` attachment points) raise heterogeneous, version-dependent exceptions (`IndexError`, `ValueError`, `AtomValenceException`, ...). A single such failure previously raised and terminated the whole run.

## Approach

Per-SMILES failures are scored as NaN so a bad fragment can never kill a run. The exception handling is deliberately broad (not a fixed tuple): the raised exception types are heterogeneous and RDKit's sanitize exceptions do not always subclass `ValueError`, so a fixed tuple would reintroduce crashes.

To avoid masking real bugs:
- the full traceback is logged for every failed SMILES (`exc_info=True`), so genuine bugs stay diagnosable;
- if **every** input in a batch fails to score, that is flagged as a likely component/configuration bug rather than per-SMILES noise (empty batches excluded).

## Changes
- `comp_linkinvent.py`: guard `None` from `cap_fragment`; per-SMILES NaN scoring with full-traceback logging and a systemic-failure flag.
- `comp_physchem.py` / `comp_rdkit_descriptors.py`: same `None`-molecule guard; the descriptors guard uses `number_of_endpoints` (the bound `CalcDescriptors` method exposes no `propNames`).

## Tests
- regression tests: unparseable and multi-bonded-attachment fragments score NaN (not crash) across all fragment components; `None`-molecule guards in physchem/descriptors; all-fail batches flagged loudly; empty batch clean.

`pytest` on the linkinvent/physchem/descriptors suites -> 12 passed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee0d56f4a074`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.