# Issue

**Title:** Added Buddies to Options and Plots

## Description

Part of #3184

### Summary

-  Adds `buddy` properties to 15 field labels across `pdfoptionsdialog.ui`, `xrdoptionsdialog.ui`, `displacementdialog.ui`, `vibrationdialog.ui`, `chargedialog.ui`, `bondingdialog.ui`, and `lineformatinputdialog.ui` so screen readers announce each field with its label.
-  Skipped `modesLabel` and `summaryLabel` in `displacementdialog.ui` because they only display information and have no field to point at.
- Left all existing label text unchanged because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened the PDF Plot Options, Theoretical XRD Pattern
Options, Generate Displaced Coordinates, Vibrational Modes, Partial Charges, Bonding, and
Insert Molecule dialogs, and tabbed through the fields with Narrator. All 15 new buddy
fields are now announced with their labels before their control types and values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa2198141f73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.