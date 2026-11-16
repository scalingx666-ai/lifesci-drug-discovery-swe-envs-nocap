# Issue

**Title:** Fix one-atom multiple-cut matching in VariableFragmentsReducer and add tests

## Description

and #83.

**`VariableFragmentsReducer`**: with the Rf/Db/Sg attachment masks, RDKit writes the central carbon in brackets (`*[CH]([Rf])[Db]`, `*[C]([Rf])([Db])[Sg]`), so the hard-coded `_oneAtom_multipleCuts` strings never matched. Transformations with 2 or 3 cuts on one atom, e.g. `[*:1]C([*:2])c1ccccc1>>[*:1]C([*:2])c1ccncc1`, were then treated as reducible and dropped by `--smallest-transformation-only`. The strings are now built from RDKit's canonical SMILES.

**`_iter_num_atoms_for_radii`**: removed the `min_radius` parameter (and from `iter_num_atoms_for_radii` and `EnvironmentCache.get_or_compute_center_radii`). It did not skip the inner radii, it only truncated the result at `max_radius - min_radius`, which was the cause of #83. The only caller already passed 0.

**Tests** (`tests/test_index.py`):
- `VariableFragmentsReducer`: reducible / not reducible cases, including multiple cuts on one atom
- `get_max_constant_radius_for_fraction_transfer`: expected radii for a fixed example, `None` when `--min-radius` is not reachable, `max_frac_trans >= 1`
- `mmpdb index` with `--min-radius` and `--max-frac-trans`: no rules without environments, and `--min-radius 1` gives the same pair environments as `--min-radius 0` restricted to radius >= 1
- `mmpdb index --smallest-transformation-only`

Against the code before #82/#83, 9 of the 11 new tests fail; against current master, the multiple-cuts test fails. All 135 tests pass with this branch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `736273b0258e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.