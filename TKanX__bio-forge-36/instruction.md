# Issue

**Title:** fix(ops): Refine Terminal Geometry and Decouple Local Construction from Global Alignment

## Description

### Summary:

Addresses geometric artifacts observed in reconstructed terminal atoms (N-terminal hydrogens, C-terminal OXT, and nucleic acid termini). The previous implementation of `calculate_transform` was too simplistic for single/double atom alignments and relied on global SVD coupling which could distort local geometry. Additionally, terminal atom construction has been rewritten to use robust local coordinate frames based on standard bond lengths and angles, rather than rough vector approximations.

#### Cases:

##### N-terminal: Amino Group (NH3+)

![Image](https://github.com/user-attachments/assets/2a3369ca-72fb-4718-a8ec-0bac73d0d1f3)

##### C-terminal: Carboxylate Ion Group (COO-)

![Image](https://github.com/user-attachments/assets/309ab486-3ee5-421d-8863-4424e4003cac)

##### C-terminal: Carboxylate Group (COOH)

![Image](https://github.com/user-attachments/assets/922fbd7e-642f-4bf7-a080-3786d72bac59)

### Changes:

- **Enhanced `construct_n_term_hydrogens`:**
  - Now uses a local sp³ frame built from the N and CA atoms (and a reference vector) to place H1, H2, and H3.
  - Enforces a standard N-H bond length of 1.01 Å and tetrahedral angles (109.5°), replacing the previous approximate direction logic.
  - Supports staggered conformations (0°, 120°, 240°) for protonated amines.

- **Refined `construct_c_term_hydrogen`:**
  - Implemented `place_hydroxyl_hydrogen` helper to position the HOXT atom with precise geometry (0.97 Å bond length, 109.5° angle, and 60° torsion).
  - Uses the carboxyl plane (defined by C, O, and CA) to orient the hydrogen correctly relative to the OXT atom.

- **Improved Nucleic Acid Termini (`construct_3_prime_hydrogen`, `construct_5_prime_hydrogen`):**
  - Updated both functions to use `place_hydroxyl_hydrogen` for consistent O-H bond geometry.
  - Ensures 3'-OH and 5'-OH groups are placed with correct bond lengths and tetrahedral angles relative to the sugar ring.

- **Robust 5'-Phosphate Protonation (`construct_5_prime_phosphate_hydrogens`):**
  - Implemented correct sp³ geometry for the HOP3 proton on terminal phosphates.
  - Positions the hydrogen at 0.96 Å from OP3 with a 109.5° P-O-H angle, oriented 180° dihedral relative to the P-O bond vector.

- **Decoupled SVD Alignment:**
  - Refactored `calculate_transform` in `ops/repair.rs` to handle 1-point and 2-point alignments explicitly and correctly.
  - Single-point alignment now performs pure translation without inducing rotation.
  - Two-point alignment computes the minimal rotation required to align the vector without introducing arbitrary twists around that axis.
  - SVD is now reserved for cases with 3 or more points, ensuring robust least-squares fitting for bulk atoms.

- **Local Geometry Helpers:**
  - Added `build_sp3_frame` and `place_hydroxyl_hydrogen` utilities to `ops/hydro.rs`.
  - Added geometric constants (`SP3_ANGLE`, `NH_BOND_LENGTH`, etc.) to enforce physical realism.

- **Updated Tests:**
  - Added comprehensive geometric validation tests (`n_terminal_h_has_tetrahedral_geometry`, `c_terminal_hoxt_has_tetrahedral_geometry`, etc.) that check bond lengths and angles against expected physical values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9f31651e2fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.