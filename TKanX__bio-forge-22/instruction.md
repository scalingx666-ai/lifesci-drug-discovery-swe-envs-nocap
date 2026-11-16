# Issue

**Title:** feat(ops): Enhance Histidine Protonation Strategy with H-Bond Angle Checks

## Description

### Summary:

Enhances the `ops::hydro` module by improving the `HisStrategy::HbNetwork` logic. Previously, this strategy only considered the presence of acceptor atoms within a certain distance. Now, it incorporates hydrogen bond angle constraints to more accurately predict the likely protonation state of histidine residues based on their local chemical environment. This leads to more physically realistic protonation assignments, which is critical for accurate molecular dynamics simulations and biochemical analysis.

### Changes:

- **Improved Histidine Protonation Logic (`ops::hydro`):**
  - The `select_neutral_his` function now accepts an optional `Grid` of potential acceptor atoms and the current residue's indices.
  - A new helper function, `calculate_h_bond_score`, was introduced to quantify the plausibility of hydrogen bonds. This function evaluates both distance (below 2.5Å) and angle (> 120° N-H···A) constraints for potential bonds.
  - The `HisStrategy::HbNetwork` now uses these scores to determine the most likely protonation state by comparing the predicted scores for the HID and HIE tautomers. The tautomer with the higher total H-bond score is chosen.

- **Spatial Grid Integration:**
  - The `add_hydrogens` function now builds a `SpatialGrid` containing all nitrogen and oxygen atoms (potential acceptors) when the `HisStrategy::HbNetwork` is selected.
  - This grid is passed down to `select_neutral_his` to facilitate efficient neighbor searching for H-bond candidates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d5d31ba4f4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.