# Issue

**Title:** #7681-monomer creation works wrong

## Description

Problem                                                                                                                                                                                                                               
When a user creates a monomer via the monomer wizard in Molecules mode (e.g. from SMARTS -[#6]), collapses it, and then deletes the bond connecting the monomer to its leaving-group H atom, hovering over the collapsed monomer shows "H" in the preview tooltip instead of the correct "R1" attachment point label.

The label was only displayed correctly after a Molecules → Macromolecules → Molecules mode switch, which served as an unintentional workaround.

Root cause
The hover preview in Molecules mode is built by makeStruct() in functionalGroupsTooltip.ts. For a MonomerMicromolecule, this function was assembling the preview struct by copying atoms directly from the canvas (the live editor struct).

The canvas leaving-group H atoms created through the wizard are placed without rglabel set. The rglabel property (which drives the "R1/R2/…" label rendering) is only set on atoms inside monomerItem.struct — the monomer template by fillStructRgLabelsByMonomerTemplate. Without rglabel, the renderer falls back to the atom's element label: "H".

The mode-switch workaround worked because MacromoleculesConverter, when converting back from macromolecules to molecules mode, rebuilds the canvas atoms from the template, at which point the atoms correctly inherit rglabel.

Fix
For MonomerMicromolecule, makeStruct() now uses monomerItem.struct.clone() — the monomer template struct — as the preview source instead of copying atoms from the canvas. The template always has rglabel set correctly, regardless of the history of canvas edits.

A null-safe fallback to the original canvas-based path is retained for cases where monomerItem.struct is not available.


## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [x] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44b6cf9ebb06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.