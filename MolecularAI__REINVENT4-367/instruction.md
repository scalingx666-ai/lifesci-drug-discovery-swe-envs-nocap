# Issue

**Title:** fix: reject invalid SMARTS in MatchingSubstructure at setup

## Description

**Problem**
If a SMARTS in a `MatchingSubstructure` endpoint can't be parsed, `Chem.MolFromSmarts` returns `None` and the component adds that `None` to the endpoint's pattern list. The list is then not empty, so the existing "no valid SMARTS patterns found" check never fires. The run continues until scoring, where `mol.HasSubstructMatch(None, ...)` fails with a Boost `ArgumentError` (`Mol.HasSubstructMatch(Mol, NoneType) did not match C++ signature`) that doesn't say which pattern is wrong. When the bad SMARTS sits in a list of alternatives, the crash waits for the first molecule that doesn't match an earlier pattern.

**Repro**
```python
from reinvent_plugins.components.RDKit.comp_matching_substructure import Parameters, MatchingSubstructure
ms = MatchingSubstructure(Parameters(["C(("], [False]))  # succeeds, patterns == [[None]]
ms(["CCO"])                                             # ArgumentError
```

**Change**
Check each SMARTS when the component is set up and raise `ValueError: ...: invalid SMARTS pattern 'C(('` if it can't be parsed. This works for a single SMARTS and for a list. I raise the error instead of dropping the pattern because dropping an endpoint would shift the later endpoints onto the wrong names, transforms and `use_chirality` values.

**Tests**
Added `test_comp_matching_invalid_smarts`, which covers a single invalid SMARTS and an invalid SMARTS inside a list. It fails on main and passes with the fix. `tests/reinvent_plugins/unit_tests` and `tests/scoring/unit_tests` pass, except `test_comp_mol_volume`, which already fails on main with my RDKit version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1f0ae4307a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.