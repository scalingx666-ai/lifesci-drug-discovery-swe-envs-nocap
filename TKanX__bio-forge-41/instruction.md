# Issue

**Title:** fix(ops): Correct N-Terminal Proline Hydrogen Geometry

## Description

### Summary:

Fixed a bug where N-terminal Proline residues were incorrectly assigned three hydrogens (H1, H2, H3) with a standard primary amine sp³ geometry. Proline has a secondary amine due to its pyrrolidine ring, so its N-terminus should only receive two hydrogens (H2, H3) when protonated, and one (H2) when deprotonated. The geometry calculation has been updated to correctly place these hydrogens based on the angle bisector of the CA-N-CD bonds, respecting the ring structure.

### Changes:

- **Updated `construct_n_term_hydrogens` in `ops/hydro.rs`:**
  - Added a specific branch for `StandardResidue::PRO`.
  - For N-terminal Proline, the code now calculates the direction for H2 and H3 using the bisector and perpendicular vectors of the N-CA and N-CD bonds.
  - H1 is never added to Proline.
  - H3 is only added if the terminus is protonated (pH < 8.0).

- **Added Validation Tests:**
  - Introduced `n_terminal_pro_residue` helper for generating test cases.
  - Added tests to verify correct protonation states for N-term PRO with and without specified pH (`pro_n_terminal_defaults_to_protonated_without_ph`, `pro_n_terminal_remains_protonated_below_pka`, `pro_n_terminal_deprotonates_above_pka`).
  - Added geometric validation tests (`pro_n_terminal_h_has_tetrahedral_bond_lengths`, `pro_n_terminal_h_has_tetrahedral_bond_angles`) to ensure the newly placed hydrogens satisfy the expected 1.01 Å bond length and ~109.5° tetrahedral angles relative to the CA and CD atoms.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11626b4856e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.