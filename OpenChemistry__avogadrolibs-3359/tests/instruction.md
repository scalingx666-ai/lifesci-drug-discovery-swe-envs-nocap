# Issue

**Title:** Added Buddies to insertpeptidedialog.ui and insertdnadialog.ui

## Description

Part of #3184

### Summary

- Adds `buddy` properties to the field labels in `qtplugins/insertpeptide/insertpeptidedialog.ui` and `qtplugins/insertdna/insertdnadialog.ui` so screen readers announce each field with its label.
- Insert 7 of the 9 `QLabel's for `insertpeptidedialog.ui` now have a buddy pointing at their corresponding input widget (heading for the 20 residue tool buttons) and `"Stereochemistry:" ` (sits above the `L` and `D` radio buttons, which carry their own text).
-  2 of the 4 `QLabel's for `insertdnadialog.ui` now have a buddy and `"Strands:" ` (sits next to the `Single` and `Double` radio buttons). `typeComboBox` (DNA/RNA) and `bpTurnsSpin` (the numeric spin box next to `bpCombo`) do not have separate `QLabel's in the `.ui` file.
- Left all existing label text unchanged because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened  Build, Insert, Peptide and  Build, Insert, DNA/RNA and tabbed through the fields with Narrator. Fields with buddies are now announced with their label before their control type and value.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06b2e747c2e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.