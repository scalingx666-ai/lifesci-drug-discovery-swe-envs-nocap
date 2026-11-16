# Issue

**Title:** Fix: `make_mol(reorder_atoms=True)` silently scrambles atom order

## Description

> [!NOTE]
> This PR was handled by Claude Code with Opus 4.8 under @craabreu's supervision

## Summary

`make_mol` reorders atoms by atom map number using `np.argsort`, whose default algorithm (`kind="quicksort"`, actually introsort) is **not stable**. Every unmapped atom has map number `0`, so any molecule with 17 or more atoms and no (or only partial) atom mapping — including every molecule built with `add_h=True`, since added hydrogens are always unmapped — could have its atom indices permuted arbitrarily by `reorder_atoms=True`, even though nothing needed to move.

This is silent: the molecule itself is unaffected (same canonical SMILES), so no test that checks structure would notice. What changes is the **atom indexing**, and chemprop has data that is positionally aligned to it — `MolAtomBondDatapoint.atom_y`, `V_f`/`V_d`, and bond-level features derived from atom indices. A user doing atom-level prediction on unmapped SMILES could have their targets silently paired with the wrong atoms.

The blast radius is larger than it looks because `MolAtomBondDatapoint.from_smi` defaults to `reorder_atoms=True`, and `--reorder-atoms` is a documented CLI flag with no check that atom map numbers were actually supplied.

## Fix

One-line change in `chemprop/utils/utils.py`:

```python
new_order = np.argsort(atom_map_numbers, kind="stable").tolist()
```

`kind="stable"` selects a stable sort (radix/merge), so atoms sharing a map number (most commonly `0`) keep their existing relative order. For molecules where every atom-map number is already unique, this is a no-op — the sort result was already fully determined, so no previously correct behavior changes.

## Tests added

`tests/unit/utils/test_utils.py`:

- `test_reorder_atoms_no_atom_map_large` — a 19-atom unmapped molecule (diphenhydramine) must come out in the same atom order regardless of `reorder_atoms`. (Needs ≥17 atoms to actually exercise the unstable branch of NumPy's sort — smaller molecules pass even against the bug.)
- `test_reorder_atoms_partial_map` — unmapped atoms (key `0`) keep their relative order and sort ahead of mapped atoms.
- `test_reorder_atoms_add_h` — `add_h=True` combined with `reorder_atoms=True` must not shuffle the added hydrogens.

All four new/existing `make_mol` tests were verified to fail against the unfixed code before the fix was applied, then pass after.

## Compatibility note

A model trained with atom/bond-level targets on unmapped or partially-mapped SMILES under the old, unstable behavior will not reproduce the same atom ordering after this fix. That's the point of the fix, but worth calling out for anyone with saved checkpoints or cached features from before this change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45e211af1980`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.