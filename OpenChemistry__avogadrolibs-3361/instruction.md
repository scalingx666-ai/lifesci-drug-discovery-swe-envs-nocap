# Issue

**Title:** Add Buddies to Tool Panels

## Description

Part of #3184

### Summary

-  Adds `buddy` properties to the field labels in `qtplugins/editor/editortoolwidget.ui`, `qtplugins/selectiontool/selectiontoolwidget.ui`, and `qtplugins/templatetool/templatetoolwidget.ui` so screen readers announce each field with its label.
- `editortoolwidget.ui`: both `QLabel`s now have a buddy: `"Element:"` links to `element` and `"Bond Order:"` links to `bondOrder`.
- `selectiontoolwidget.ui`: both `QLabel`s now have a buddy: `"Apply Color"` links to `applyColorButton` and `"Change Layer"` links to `changeLayerDropDown`.
- `templatetoolwidget.ui`: all 6 `QLabel`s now have a buddy. On the Centers tab, `"Element:"`, `"Formal Charge:"`, and `"Coordination:"` link to `elementComboBox`, `chargeSpinBox`, and `coordinationComboBox`. On the Ligands tab, `"Type:"` and `"Ligand:"` link to `typeComboBox` and `ligandComboBox`. On the Groups tab, `"Group:"` links to `groupComboBox`.
- Left all existing label text unchanged because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), selected the Draw (`Ctrl+2`), Template (`Ctrl+3`), and Selection (`Ctrl+4`) tools to open their tool panels, and tabbed through the fields with Narrator (including each tab of the Template tool). All 10 fields are now announced with their labels before their control types and values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e19c8cae8221`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.