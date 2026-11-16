# Issue

**Title:** feat(ops): Implement Context-Aware Histidine Protonation and Refine pH Handling

## Description

### Summary:

Significantly enhances the hydrogenation pipeline (`ops::hydro`) by introducing context-aware histidine protonation logic. It now detects potential salt bridges between histidine residues and nearby carboxylate groups (ASP⁻, GLU⁻, C-terminal COO⁻), automatically converting them to the doubly protonated HIP state when geometrically favorable. Additionally, the pH handling logic has been refined to allow users to opt-out of automatic protonation state changes by omitting the `--ph` flag, preserving original residue names while still adding hydrogens.

### Changes:

- **Enhanced Histidine Protonation:**
  - Implemented `his_forms_salt_bridge` to detect geometric proximity (default 4.0Å) between HIS nitrogens (ND1/NE2) and carboxylate oxygens.
  - Added logic to automatically assign the HIP state when a salt bridge is detected, overriding pH or strategy settings (unless disabled).
  - Introduced `his_salt_bridge_protonation` flag to `HydroConfig` to control this behavior.

- **Refined pH Handling Logic:**
  - Decoupled `add_hydrogens` from mandatory pH inputs.
  - If `target_ph` is `None`:
    - Non-histidine residues retain their original names (e.g., ASP stays ASP).
    - Histidines are only modified if salt bridge detection triggers HIP assignment.
    - Termini assume default physiological states (protonated N-term, deprotonated C-term) unless overridden by explicit pKa checks.
  - Introduced explicit pKa constants for all titratable residues (ASP, GLU, LYS, ARG, CYS, TYR, HIS).

- **Optimized Grid Structures:**
  - Created specialized grid builders: `build_carboxylate_grid` for salt bridge detection (tracking COO⁻ groups) and `build_acceptor_grid` for H-bond network analysis.
  - These grids are computed in parallel using `rayon` when available.

- **CLI and WASM Updates:**
  - Updated the `hydro` command to accept `--no-his-salt-bridge`.
  - Updated WASM bindings to expose the new configuration option.
  - Enhanced UI components (`Input`, `Select`, `Checkbox`) to support description text for better user guidance on complex options.
  - Updated `MANUAL.md` and `ARCHITECTURE.md` to reflect the new multi-phase protonation logic.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bd1dd2f5920`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.