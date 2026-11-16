# Issue

**Title:** feat(ops): Randomize Orientation of Crystal Waters During Hydrogenation

## Description

### Summary:

Introduces random orientation for crystal waters (`HOH`) during the hydrogenation process. Previously, the orientation of reconstructed water hydrogens was deterministic, leading to an artificially uniform solvent structure. By applying a random rotation to each water molecule that is being re-hydrogenated, we now generate a more diverse and physically plausible solvent environment.

### Changes:

- **Enhanced Hydrogenation Logic for Water:**
  - In `ops::hydro::construct_hydrogens_for_residue`, added logic to specifically detect when the residue being processed is a water molecule (`StandardResidue::HOH`).
  - For each water molecule, a new random `Rotation3` matrix is now generated.

- **Updated Geometry Reconstruction:**
  - The `reconstruct_geometry` function was updated to accept an optional `rotation_override: Option<Rotation3<f64>>`.
  - When a `rotation_override` is provided and the system is geometrically under-constrained (e.g., a water molecule with only one "O" anchor atom), the function now uses the provided random rotation.
  - This avoids a deterministic orientation and correctly positions the hydrogens by recalculating the translation based on the new random rotation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d5d31ba4f4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.