# Issue

**Title:** fix constrain handling for docking

## Description

This pull request introduces a new module, `xtb_geometry_terms`, to centralize and standardize the suspension and restoration of global geometry terms (such as fixed atoms and constraints) during subsystem calculations. The changes refactor existing code to use this new module, remove duplicated logic, and add targeted tests to ensure correct handling of constraints in docking scenarios.

**Key changes:**

### Geometry terms management

* Introduced a new module, `geometry_terms.f90`, which defines the `geometry_state_type` and provides `suspend_geometry_terms` and `restore_geometry_terms` routines for managing global geometry terms during subsystem calculations.
* Updated both the docking (`search_nci.f90`) and ONIOM (`oniom.F90`) modules to use the new geometry terms module, replacing previously duplicated type definitions and subroutines for suspending/restoring geometry terms. [

### Refactoring and code cleanup

* Removed the old, duplicated definitions of `geometry_state_type`, `suspend_geometry_terms`, and `restore_geometry_terms` from `oniom.F90`, consolidating this logic into the new shared module.

### Docking logic improvements

* Modified the docking search logic in `search_nci.f90` to correctly suspend global geometry terms before monomer calculations and restore them afterward, ensuring that constraints/fixed atoms for the complex do not affect monomer energies.
* Cleaned up the GFN-FF restart logic to clarify that constraints should be suspended by the caller, not read/applied within the subroutine.

### Testing

* Added new unit tests to verify that constraints/fixed atoms are handled correctly in docking scenarios, specifically ensuring that monomer energies are not affected by constraints applied to the complex and that geometry terms are restored after calculations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe7bc9e2f444`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.