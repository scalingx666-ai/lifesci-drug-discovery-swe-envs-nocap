# Issue

**Title:** feat(ops): Implement Operations Module for Structure Manipulation

## Description

### Summary:

Introduced a comprehensive `ops` (Operations) module to provide a suite of tools for manipulating and preparing biomolecular structures. This includes functionalities for cleaning, repairing, adding hydrogens, solvating, and building molecular topologies. It also provides a robust transformation API for geometric manipulations. These operations form the core toolkit for preparing structures for simulation and analysis.

### Changes:

- **Established `ops` Module Framework:**
  - Created a new top-level `ops` module to house structure manipulation logic.
  - Defined a dedicated `ops::error::Error` enum to provide specific and informative error types for operational failures.

- **Implemented Structure Cleaning (`ops::clean`):**
  - Developed a `clean_structure` function with a flexible `CleanConfig` to selectively remove components.
  - Added options to remove water, ions, heteroatoms, hydrogens, and specific residues by name, with a `keep_residue_names` list to override removal rules.
  - Enhanced the `Structure` and `Chain` models with `retain_residues` and `prune_empty_chains` methods to support filtering.

- **Implemented Structure Repair (`ops::repair`):**
  - Created a `repair_structure` function that reconstructs missing heavy atoms in standard residues based on their templates.
  - Implemented functionality to remove any atoms not defined in the corresponding residue template.
  - Utilizes Singular Value Decomposition (SVD) for robust 3D alignment of partial residues against their templates to accurately place missing atoms.

- **Implemented Hydrogen Addition (`ops::hydro`):**
  - Developed an `add_hydrogens` function with a `HydroConfig` to manage protonation states and placement strategies.
  - Implemented logic to determine residue protonation states based on target pH and pKa values for titratable groups (e.g., ASP/ASH, LYS/LYN).
  - Added multiple strategies for determining neutral Histidine states (`HID`, `HIE`), including a hydrogen-bond network optimization approach.
  - Implemented automatic detection and handling of disulfide bridges (relabeling CYS to CYX).

- **Implemented Solvation (`ops::solvate`):**
  - Created a `solvate_structure` function to place the solute in a periodic box and fill it with water molecules.
  - Implemented a spatial grid system to efficiently place water molecules on a grid while avoiding steric clashes with the solute.
  - Added functionality to neutralize the system charge by replacing water molecules with specified cations and anions.

- **Implemented Topology Building (`ops::topology`):**
  - Introduced a `TopologyBuilder` to construct a `Topology` object from a `Structure`.
  - Implemented logic to build intra-residue bonds based on standard and user-provided hetero templates.
  - Added detection of inter-residue bonds, including peptide bonds, nucleic acid backbone linkages, and disulfide bridges, based on distance cutoffs.

- **Implemented Geometric Transformations (`ops::transform`):**
  - Created a `Transform` struct with static methods for common geometric operations.
  - Implemented functions for translation, rotation (per-axis and Euler angles), and centering (by geometry or center of mass).
  - Rotations correctly update both atom coordinates and simulation box vectors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f97246bb38b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.