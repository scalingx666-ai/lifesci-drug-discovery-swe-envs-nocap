# Issue

**Title:** Mordred: remove the helpers the vectorized descriptors no longer use

## Description

Now that every descriptor reads its atom properties from the `AtomicProperties` arrays, a set of per-atom helpers has no callers left. This PR removes them. No descriptor code changes.

**Removed**
- `utils/atomic_properties.py`:
  - The scalar per-atom getters: `get_element_symbol`, `get_atomic_number`, `get_mass`, `get_van_der_waals_radius`, `get_van_der_waals_volume`, `get_{sanderson,pauling,allred_rochow}_electronegativity`, `get_polarizability` and `get_ionization_potential`. `ELEMENT_PROPERTY_MATRIX` replaced them.
  - `get_vertex_degree`, `get_valence_vertex_degree` and `get_intrinsic_state`. The `AtomicProperties` arrays `vertex_degree`, `valence_vertex_degree` and `intrinsic_state` replaced them. Their literature references now sit in the comment on `vertex_degree` and in the docstrings of `AtomicProperties._valence_vertex_degree` and `_intrinsic_state`.
  - The unused `VAN_DER_WAALS_RADII` import. The constant itself stays in `periodic_table.py`, because `sasa.py` uses it.
- `utils/periodic_table.py`: `POLARIZABILITY_78`, together with its data file `polarizalibity78.txt`. Only the 94-element table is used.
- `tests/.../rdkit_descriptors.py`: the unused `RDKIT_2D_FEATURE_NAMES` and `RDKIT_3D_FEATURE_NAMES` constants.

**Tests**
The vertex degree, valence vertex degree and intrinsic state reference-value tests now check `AtomicProperties(mol).<property>[1]`, which is the code the descriptors run. Their expected values and parametrization are unchanged.

**Intentionally kept**
- `get_atomic_number_from_symbol` and `get_gasteiger_charge`: still used.
- `chi.SUBGRAPH_TYPES` and `Subgraphs._subgraph_bond_idxs`: only the subgraph tests use them. `_subgraph_bond_idxs` exposes the raw enumerated subgraphs, which the RDKit cross-check of the enumeration needs.

I also checked the rest of `_new_mordred` for unused code (vulture, a cross-reference of every definition, ruff's unused-code rules). Nothing else came up, and every file in `utils/data/` is still loaded.

---

The last piece of the #661 split. It is now detached from that stack and rebased onto the current `mordred`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0288aab7ea7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.