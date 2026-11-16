# Issue

**Title:** fix(ops): Prevent Duplicate Bonds in Topology Builder

## Description

### Summary:

Fixed a bug in the `TopologyBuilder` where bonds involving hydrogens could be created twice: once from the template's `bonds` section and again from the `hydrogens` section's anchor information. This PR introduces a `BondCollector` with a `HashSet` to ensure each bond is inserted only once, guaranteeing correct atom degrees in the final `Topology`.

### Changes:

- **Introduced `BondCollector`:**
  - Created a new internal `BondCollector` struct within `ops/topology.rs` to manage bond collection.
  - The collector uses a `HashSet` to track seen `(atom1_idx, atom2_idx, order)` tuples, ensuring that `Bond::new` canonicalization is respected and only unique bonds are added to the final list.

- **Refactored `TopologyBuilder`:**
  - Replaced the mutable `Vec<Bond>` argument in `build_intra_residue` and `build_inter_residue` with a `&mut BondCollector`.
  - All bond creation logic now calls `collector.insert()` instead of `bonds.push()`, automatically enforcing uniqueness.

- **Removed Redundant Hydrogen Bonding Logic:**
  - Removed the explicit loop that created bonds between hydrogens and their first anchor atom. This logic is now redundant, as these bonds are expected to be defined in the template's main `bonds` section. The `BondCollector` would have deduplicated them, but removing the source of the duplication is a cleaner fix.

- **Added Validation Tests:**
  - Added a new unit test (`build_avoids_duplicate_bonds_for_standard_residue`) to verify that a standard residue's topology contains no duplicate bonds.
  - Added a test (`build_sets_expected_water_degree`) to confirm that water molecules are correctly built with exactly two O-H bonds, a common case where the duplication bug was previously observed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48138d571fde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.