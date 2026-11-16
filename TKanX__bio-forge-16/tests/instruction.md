# Issue

**Title:** fix(ops): Add Support for 5'-Terminal Nucleic Acid Phosphates

## Description

### Summary:

Enhances the `repair`, `hydro`, and `topology` operations to correctly handle 5'-terminal nucleic acid residues, both with and without phosphate groups. The repair step now synthesizes the missing `OP3` atom for phosphorylated termini, and the hydrogenation step correctly titrates this group based on pH. Topology building rules have also been updated to include the necessary terminal bonds.

### Changes:

- **Enhanced `ops::repair` for Nucleic Acids:**
  - The `repair_residue` function now detects 5'-terminal nucleic acids that contain a phosphorus (`P`) atom.
  - For such residues, it synthesizes the missing `OP3` atom using tetrahedral geometry, completing the terminal phosphate group.
  - For 5'-terminal residues *without* a `P` atom, the repair logic now correctly removes any phosphate atoms defined in the template (`P`, `OP1`, `OP2`), ensuring a clean 5'-hydroxyl terminus.

- **Improved `ops::hydro` for Nucleic Acid Termini:**
  - The `add_hydrogens` function now distinguishes between phosphorylated and non-phosphorylated 5'-termini.
  - If a phosphate group is present, it adds a `HOP3` hydrogen to the `OP3` atom only if the pH is below the phosphate pKa₂ (≈6.5), correctly modeling the charge state.
  - If no phosphate is present, it adds a `HO5'` hydrogen to the `O5'` atom, forming a terminal hydroxyl group.

- **Updated `ops::topology` Builder:**
  - The `TopologyBuilder` now correctly identifies and builds bonds for 5'-terminal phosphate groups, including `P-OP3` and the pH-dependent `OP3-HOP3`.
  - The logic for optional terminal atoms was updated to correctly handle atoms that are conditionally present based on phosphorylation state (`OP3`, `HOP3`) or its absence (`HO5'`).

- **Documentation Updates:**
  - Updated `ARCHITECTURE.md` and `MANUAL.md` to reflect the new capabilities for handling nucleic acid termini in the repair and hydrogenation pipelines.
  - Updated `README.md` to mention the new repair capability for 5'-phosphorylated nucleic acids.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74e8200eccf2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.